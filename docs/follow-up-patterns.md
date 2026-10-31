# Follow-Up Sequence Patterns

Patterns for the follow-up stage of the pipeline in [architecture.md](architecture.md). Follow-up exists because most leads do not book on the first conversation. Its job is to be useful and easy to answer, not to be persistent noise.

These are patterns, not send-ready scripts. Write the actual wording per business, per channel, and per lead, using what that lead actually said.

## Principles

- **Value first.** Every follow-up gives something: an answer, a useful detail, a relevant example, a simpler next step. A message whose only content is checking in should not be sent.
- **Specific to the lead.** Reference their service, location, timeline, or the problem they described. If a message could be sent unchanged to fifty people, it is not ready.
- **One clear ask.** Each message ends with a single low-effort next step: a yes or no question, two time options, or a direct booking link. Never three asks in one message.
- **Easy exit.** Every sequence respects opt-outs immediately and forever, see below. Staying in a sequence is never the path of least resistance versus leaving it.
- **Fewer, better messages.** The ladder below is a maximum, not a quota. A lead who books, replies, or opts out leaves the sequence at that moment.

## Timing ladder

For a qualified lead who has gone quiet after the first conversation:

| Touch | When | Purpose |
|---|---|---|
| 1 | Same day, a few hours after the last message | Answer anything outstanding and restate the simple next step |
| 2 | Next day | Add value: a detail, example, or clarification tied to their problem |
| 3 | Day 3 to 4 | Reduce friction: offer two concrete times or the booking link again |
| 4 | Day 7 | Final nudge for this cycle: clear close, door left open, sequence ends if no reply |

Adapt the clock to the lead's stated timeline. A lead who said "next month" should not be on a day 3 nudge about this week. A lead with an urgent deadline may justify a faster first touch, written by or approved by a human.

After touch 4 with no reply, the lead moves to a reactivation date. It does not keep receiving messages.

## Message patterns by stage

### No-reply nudge (during qualification)

The lead stopped answering mid-qualification.

- Pick up the exact thread: reference the last question or their last point, not a fresh opener.
- Make the reply smaller: turn an open question into a choice between two options where possible.
- One nudge only in this state. If it gets no reply, stop, keep the record complete, and let the timing ladder above decide the next touch.

### Warm follow-up (qualified, not booked)

The lead is a fit and has the full picture but has not booked.

- Lead with value connected to their problem: how a similar situation was handled, a detail they asked about indirectly, a deadline that genuinely affects them.
- Restate the booking step in one line, with the link or the two time options.
- Different angle each touch. Repeating the same message with "just following up" added is not a sequence.

### Booking reminder (booked, appointment ahead)

The lead has booked. The risk now is a no-show, not silence.

- Confirmation at booking: what, when, where or which link, and who they will speak to.
- Reminder the day before: same facts, plus how to reschedule in one step.
- Reminder on the day, a few hours ahead, for high-value appointments only.
- A missed appointment gets one human-reviewed message offering new times. No guilt, no automated chase after that.

### Reactivation (30, 60, 90 days)

For NURTURE and Lost (unresponsive) leads, on the reactivation cycle from the architecture doc:

- **30 days:** a genuinely new reason to talk: a relevant change, a seasonal point that affects their service, or the answer to something they raised. If there is no real reason, skip this cycle.
- **60 days:** a short, direct check that their situation has not changed, with the reply made as easy as a single word. One message.
- **90 days:** a clean closing message: checking in one last time, happy to help if the timing is better now, and they will not hear more unless they reply.
- Maximum three reactivation cycles for a lead, then the record goes dormant with a note of what would make it worth reopening. Reactivation is a courtesy, not a subscription.

## Cold context rule

Where a sequence is effectively cold outreach, for example messaging a lead who never replied to the very first contact, the limit is stricter: **maximum 2 follow-ups** after the initial message, then stop. Warmth has to be earned by engagement; volume is not a substitute for it. This mirrors the cold outreach follow-up cap used in the wider TechAura playbooks.

## Opt-out and STOP handling

- Any clear opt-out stops everything: STOP, unsubscribe, "not interested", "leave me alone", or an equivalent in any wording. Interpret generously in the lead's favour. Ambiguity stops the sequence too.
- Stopping is immediate and permanent for that channel, and applies across sequences. A lead who opted out of follow-ups does not get reactivated at 30 days.
- Confirmation: one short message confirming they have been opted out is appropriate on channels where that is normal practice, and nothing after it. No win-back attempt inside the confirmation.
- The opt-out is written to the CRM record with its date, and the record's next action is cleared. An opted-out lead with a scheduled touch still in the system is a defect.
- Opt-outs are honoured within 24 hours at the absolute latest as a policy ceiling; the automation target is immediate, at the moment the message is processed.

## Tone rules

- Write like a person on the business's team, not like a system. Natural sentences, contractions where the brand uses them, no hype.
- No pressure tactics: no false scarcity, no invented deadlines, no guilt, no repeated urgency escalation across touches.
- No generic mass-message language. If the business name, the service, or the lead's own words could be swapped out without changing the message, rewrite it.
- Keep the business's standard sign-off and naming rules consistent with its other channels. For TechAura's own outreach that means signing as the team, never as an individual.
- Match the channel: short for DM and WhatsApp, slightly fuller for email, always readable on a phone.
- If a follow-up needs an apology, an exception, a discount, or a judgement call, a human writes it. Automation escalates, it does not improvise around problems.

## What good looks like

A follow-up system is working when replies, including no thanks, go up and complaints stay at zero. Track per sequence: sends, replies, bookings, opt-outs. An opt-out spike on a specific touch means that touch is wrong, and it gets rewritten or dropped, not sent harder.
