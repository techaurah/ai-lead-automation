# AI Lead Automation — by TechAura

A practical blueprint for automating lead handling for service businesses: capture, instant reply, AI qualification, CRM write, follow-up, and booking.

> Built by [TechAura](https://techaurah.com) — AI & Software Engineering. This repository documents the architecture and provides starter workflow patterns. Adapt the prompts, fields, and steps to your own stack.

## The problem

Service businesses lose leads they already paid to generate:

- A new inquiry arrives after hours and gets no reply until morning
- Replies are slow, inconsistent, or forgotten
- No qualification, so the team spends equal time on every lead
- Leads live in DMs and inboxes, not in a CRM
- No follow-up sequence, no booking link, no reporting

## The system

```
Lead arrives (Instagram DM / web form / WhatsApp / email)
        |
        v
Instant AI reply (under 60 seconds, on-brand, 24/7)
        |
        v
AI qualification (service, location, timeline, budget signals)
        |
        v
CRM write (contact, source, score, stage, notes)
        |
        v
Follow-up sequence (no-reply nudges, value first)
        |
        v
Booking (calendar link, confirmation, reminder)
        |
        v
Reporting (volume, response time, conversion)
```

## Lead scoring (0-100)

| Signal | Points |
|---|---|
| Clear problem stated | 20 |
| Service fit | 20 |
| Potential value | 15 |
| Business size | 10 |
| Ability to pay | 10 |
| Decision-maker access | 10 |
| Urgency | 10 |
| Recent activity | 5 |

HOT 80+, WARM 65-79, NURTURE 50-64.

## Repository contents

- [Architecture and data model](docs/architecture.md) for the pipeline above
- [Qualification prompt patterns](docs/qualification-prompts.md) (channel-agnostic)
- [CRM field mapping examples](docs/crm-field-mapping.md)
- [Follow-up sequence patterns](docs/follow-up-patterns.md)
- [LICENSE](LICENSE)

## Stack this works with

n8n or Zapier for orchestration, an LLM for reply and qualification, your existing CRM and calendar. No platform lock-in: the value is the flow, not a single tool.

## License

MIT. See [LICENSE](LICENSE). Businesses and builders are welcome to adapt the documentation and patterns in this repository for their own use.

---

TechAura — https://techaurah.com — Software. Intelligence. Automation.

## About TechAurah

TechAurah is an AI & Software Engineering company building AI products, agents, and intelligent automation for businesses in the USA, UK, UAE, Canada, Australia, and Europe.

We are available for AI engineering projects: https://techaurah.com
