# CRM Field Mapping

How the lead data model from [architecture.md](architecture.md) maps into the CRMs small businesses actually use. The pipeline fields are the source of truth for meaning; each CRM section translates them into that system's objects and properties.

General rules for every CRM:

- Write the pipeline field to the closest native field first. Use a custom field only when no native equivalent exists, and name it clearly, for example `TA Lead Score`, not `Field 12`.
- A lead is normally two linked objects: a **contact** (the person) and a **deal** (the opportunity). Contact facts go on the contact, pipeline facts go on the deal.
- Never overwrite a human-entered value with an automation value without checking. Automation updates its own fields and appends notes; humans keep theirs.
- Every automation write adds an activity or note entry stating what happened and when, so the record explains itself.

## Pipeline fields to generic CRM fields

| Pipeline field | Generic CRM location | Notes |
|---|---|---|
| `id` | Custom field on the deal, for example `Lead ID` | Stable external reference. Also used for dedup checks across systems |
| `source_channel` | Contact or deal `Lead Source` | Use a fixed value list: Instagram, Web Form, WhatsApp, Email, Other |
| `contact.name` | Contact `First Name` / `Last Name` | Split on the first space if only a full name is provided |
| `contact.email` | Contact `Email` | Primary dedup key, see below |
| `contact.phone` | Contact `Phone` | Store in international format where the lead provided a country context |
| `contact.social_handle` | Custom field on the contact, for example `Instagram Handle` | Dedup key for social first leads who have not shared email or phone yet |
| `service` | Deal name or a `Service` custom field on the deal | Deal name pattern: `[Service] - [Contact Name]` |
| `location` | Contact `City` plus a `Service Area` field on the deal if it differs | The job location matters more than the billing address for service businesses |
| `timeline` | Custom date or text field on the deal, for example `Requested Timeline` | Keep the lead's own words in a note alongside any normalised date |
| `score` | Custom number field on the deal, for example `Lead Score` | 0 to 100, updated on re-score |
| `score_band` | Custom dropdown on the deal: HOT, WARM, NURTURE | Drives list views and human priority queues |
| `stage` | Deal pipeline stage | Mapping table below |
| `owner` | Deal owner | The human or team responsible for the next action |
| `last_interaction` | Native `Last Activity` where the CRM maintains it, otherwise a custom date field | Updated on every message in either direction |
| `next_action` | Task title on an open task attached to the deal | One open next-action task per active deal |
| `next_action_date` | That task's due date | A deal without an open task and due date is flagged in reporting |
| `notes` | Note or activity entry on the deal | Qualification summary, promises made, handoff context |

## Platform examples

### HubSpot

- Contact properties: `email`, `phone`, `firstname`, `lastname`, `city`, `lead_source` (custom or the native `hs_lead_status` workflow, pick one and stay consistent), plus a custom contact property for the social handle.
- Deal properties: `dealname` as `[Service] - [Name]`, `pipeline` and `dealstage` per the stage mapping below, `deal_owner` via `hubspot_owner_id`, plus custom deal properties for lead score (number), score band (dropdown), requested timeline, and external lead ID.
- Tasks: HubSpot tasks attached to the deal carry `next_action` and its due date.
- Notes: use Notes objects associated with both contact and deal for qualification summaries and handoff context.

### Pipedrive

- Person fields: `name`, `email`, `phone`, plus a custom person field for the social handle.
- Organization: create or match an organization when the lead is a business; dedup on organization name and domain where provided.
- Deal fields: `title` as `[Service] - [Name]`, `person_id`, `org_id`, `user_id` as owner, `stage_id` per the mapping below, plus custom deal fields for lead score, score band, source channel, timeline, and external lead ID.
- Activities: Pipedrive activities are the natural home for `next_action` and `next_action_date`. Keep exactly one open activity as the next action per active deal.
- Notes: deal notes for qualification summaries and promises.

### GoHighLevel

- Contact fields: `firstName`, `lastName`, `email`, `phone`, plus custom fields for social handle and source detail. Use tags for source channel and score band, for example `src-instagram` and `band-hot`, so Smart Lists can segment on them.
- Opportunity fields: name as `[Service] - [Name]`, pipeline and stage per the mapping below, monetary value only when a real figure exists, plus custom opportunity fields for lead score, timeline, and external lead ID.
- Tasks and notes: contact/deal tasks for the next action and due date; notes for qualification summaries and handoff context.
- Workflows: GoHighLevel workflows can host the follow-up sequences in [follow-up-patterns.md](follow-up-patterns.md) natively; keep the stage and task rules identical so reporting stays consistent.

### Google Sheets (as the CRM)

A single workbook can run this model for a small business. One row per lead on a `Leads` tab, columns in pipeline field order:

| Column | Field |
|---|---|
| A | `id` |
| B | Created date |
| C | `source_channel` |
| D | Contact name |
| E | Email |
| F | Phone |
| G | Social handle |
| H | Service |
| I | Location |
| J | Timeline |
| K | Score |
| L | Score band |
| M | Stage |
| N | Owner |
| O | Last interaction |
| P | Next action |
| Q | Next action date |
| R | Notes |

Sheets specific rules:

- One header row, frozen, with data validation dropdowns for source channel, score band, and stage using the exact value lists above. Consistent values are what make filters and pivot summaries work.
- Never insert a row in the middle. Append new leads at the bottom so row references in other tabs stay stable.
- A `Summary` tab with simple counts by stage, band, and channel covers basic reporting without any other tool.
- Dedup in Sheets means searching the email, phone, and handle columns before appending. If a match exists, update that row instead.

## Pipeline stage mapping

| Pipeline stage | HubSpot deal stage | Pipedrive stage | GoHighLevel stage | Sheets value |
|---|---|---|---|---|
| New | Qualification | New Lead | New | New |
| Qualified | Qualification complete | Qualified | Qualified | Qualified |
| Warm | (stays Qualified, band WARM) | In Follow-up | Follow-up | Warm |
| Discovery | Appointment / Needs Analysis | Discovery Call | Discovery | Discovery |
| Proposal | Proposal / Quote Sent | Proposal Sent | Proposal | Proposal |
| Negotiation | Negotiation | Negotiation | Negotiation | Negotiation |
| Won | Closed Won | Won | Won | Won |
| Lost | Closed Lost | Lost | Lost | Lost |

Stage names inside a given CRM can be renamed to match, as long as the mapping stays one to one and every stage in the pipeline exists in the CRM. Reporting compares stages, so drift between systems breaks it silently.

## Dedup keys

Check in this order before creating any record:

1. **Email**: exact match, lowercased, trimmed. The strongest key when present.
2. **Phone**: match on digits only, with country code where known. Formatting differences are not different people.
3. **Domain**: for business leads, the company domain from an email address or website, matched against existing organizations. Consumer mail domains (gmail.com and similar) are never a dedup key on their own.
4. **Social handle**: platform plus handle, for example `instagram:@handle`. This is often the only key a DM lead has at capture.

Rules:

- A match on any key means update the existing record. Add the new interaction, refresh `last_interaction`, and re-run scoring if new signals arrived.
- A match on a weaker key alone (social handle) with a different email or phone is flagged for a human to merge, not auto-merged.
- If no key matches, create the record and write back every key the lead has provided so the next inquiry dedups correctly.
- Keep the original `source_channel` of the first record, and note later channels in the activity history. First source is what reporting attributes the lead to.
