# Qualification Prompt Patterns

Channel agnostic patterns for the AI qualification stage of the pipeline described in [architecture.md](architecture.md). The same patterns work in Instagram DMs, WhatsApp, web chat, and email. Only the message length and formality change by channel, the questions and the extraction do not.

These are patterns, not scripts. Adapt the wording to the business, its services, and its voice before use.

## Principles

1. **Diagnose before you pitch.** The job of qualification is to understand the lead's problem. Recommendations come after the picture is clear, and selling comes after a recommendation fits.
2. **One or two questions at a time.** A form disguised as a chat message loses people. Ask the next most useful question, wait, then continue.
3. **Use what they already said.** If the first message names the service and the city, do not ask for the service and the city again. Reflect it back so the lead can see they were heard.
4. **Specific over generic.** Reference the actual service, location, or problem they mentioned. Generic openers read as automation, and people disengage.
5. **Short messages.** Conversational length for chat channels. If a reply needs a paragraph, it probably needs a human.
6. **Never invent facts.** Do not state prices, availability, timelines, or guarantees that have not been provided to the system. Unknown means the system says it will confirm, and hands off.
7. **Score silently.** Qualification feeds the scoring model in the architecture doc. The lead never sees a score, a band, or criteria language.

## The intake question set

Three questions establish whether a business, or a lead conversation, has enough to work with. In lead conversations they are woven into the dialogue. In discovery about automation itself, they are the starting audit:

1. **What is your main contact channel?**
   Where inquiries actually arrive: Instagram DMs, WhatsApp, web form, phone, email. The pipeline is built around the real channel, not the assumed one.
2. **How many inquiries do you get in a typical week?**
   Volume decides how much automation is worth building and where follow-up effort pays back.
3. **What happens when an inquiry comes in at 10pm?**
   The after-hours answer exposes the biggest leak in most lead handling: who replies, how fast, and what is lost overnight. In a lead conversation the equivalent is timeline: when do you need this sorted, and what happens if it waits?

For an individual lead, the intake set translates to:

- **Service:** what exactly do you need?
- **Location:** where are you based, or where is the job?
- **Timeline:** when are you looking to get this done?
- **Context:** anything that shapes the work, such as property type, team size, or what you have already tried

Budget signals are read from context, service tier, and direct answers when the lead offers them. Do not open with a budget question.

## Example qualification dialogue structure

Structure only. Wording must be written per business and per conversation.

```
Lead:      Hi, do you do [service]? How much does it cost?

System:    Hi [name if known], thanks for reaching out. We do [service].
           So I can point you to the right option, can I ask where you
           are based and when you are hoping to get it done?

Lead:      [City]. Ideally this month, our current setup is not coping.

System:    Got it, [city] and this month. What is not coping at the
           moment, is it volume, response time, or something else?
           (Extract: service, location, timeline, problem statement.)

Lead:      [Describes problem in their words.]

System:    That makes sense, and it is exactly the kind of thing we
           handle. The next step is a short call so we can map it
           properly. Here are times that are open: [real availability].
           If none of those work, tell me what does and I will pass
           it to the team.
           (Action: score, CRM write, booking offer or handoff.)
```

Notes on the structure:

- Greeting carries a specific reference, not a template opening.
- Price questions are acknowledged, not dodged, and answered with the standard pricing if it has been provided to the system and the question is direct. Anything custom goes to a human.
- The close offers real availability. If booking is not appropriate yet, the close is a clear next step with a date, not "we will be in touch".

## Scoring extraction guidance

While the conversation runs, extract the eight scoring signals from [architecture.md](architecture.md) as structured fields, each with the quote or fact that supports it:

| Signal | Extract from |
|---|---|
| Clear problem stated (20) | The lead describing the problem in their own words |
| Service fit (20) | Requested service against the business's actual service list |
| Potential value (15) | Scope signals: size of job, number of locations or seats, repeat need |
| Business size (10) | Team size, locations, volume, when stated |
| Ability to pay (10) | Tier requested, context clues, direct statements. Evidence only |
| Decision-maker access (10) | Whether you are talking to the person who decides |
| Urgency (10) | Timeline language and deadlines |
| Recent activity (5) | The inquiry itself and any recent engagement with the business |

Rules:

- Extract only what was actually said or directly observable. An inference is marked as an inference or left out.
- Update the extraction as the conversation develops. A lead who reveals a deadline on message four is re-scored at message four.
- Keep the supporting quote with each signal. A score a human cannot trace is a score a human cannot trust.
- If two signals conflict, the more recent, more specific statement wins, and the conflict is noted for the handoff.

## Handoff triggers

Stop qualifying and hand off to a human, with the context summary described in the architecture doc, when:

- The lead asks for a person, a call with a person, or a direct contact
- The lead scores HOT (80+) and is ready to book or talk
- The request involves pricing beyond the standard offer, discounts, contracts, or anything legal
- The lead is frustrated, confused, or correcting the system
- The same question has been answered twice without progress
- The lead shares something sensitive that should not be handled by automation
- The system does not know the answer and guessing would commit the business to something

A handoff is a success state, not a failure. The automation's job is to get the right conversations to a person quickly, with context, not to hold every conversation to the end.
