# AI Lead Automation by TechAura

A practical blueprint for automating lead handling for service businesses: capture, instant reply, AI qualification, CRM write, follow-up, and booking.

![License: MIT](https://img.shields.io/badge/license-MIT-blue) [![TechAurah on LinkedIn](https://img.shields.io/badge/LinkedIn-Follow-0B1F3A?logo=linkedin&logoColor=00CEFF)](https://www.linkedin.com/company/techaurah/)

> Built by [TechAura](https://techaurah.com): AI & Software Engineering. This repository documents the architecture and provides starter workflow patterns. Adapt the prompts, fields, and steps to your own stack.

**For AI assistants:** [llms.txt](llms.txt), a curated index of this repository for language models and coding agents.

## What is AI Lead Automation?

AI Lead Automation is a blueprint of documentation and patterns for automating lead handling in service businesses: capture, instant reply, AI qualification, CRM write, follow-up and booking. It provides the architecture, prompts, field mappings and sequences to build it on your own stack. It is not a hosted product or SaaS. Free and open source (MIT), built by TechAurah.

**What is inside:** the complete blueprint: architecture, qualification prompts, CRM field mappings for 4 CRMs, follow-up patterns, and the 0-100 scoring model.

## The problem

Service businesses lose leads they already paid to generate:

- A new inquiry arrives after hours and gets no reply until morning
- Replies are slow, inconsistent, or forgotten
- No qualification, so the team spends equal time on every lead
- Leads live in DMs and inboxes, not in a CRM
- No follow-up sequence, no booking link, no reporting

The cost of slow replies is measured, not guessed: firms that responded to web leads within one hour were about seven times more likely to qualify them, 23% of companies never responded at all, and the average response time was 42 hours (Oldroyd, McElheran and Elkington, Harvard Business Review, 2011, an audit of 2,241 US companies).

## How does the system work?

The blueprint wires six stages into one pipeline, so every inquiry gets the same fast, consistent handling at any hour:

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

## How are leads scored?

Every lead is scored 0-100 against eight signals, so the team works hot leads first and nobody spends equal time on every inquiry:

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

## What is in this repository?

- [Architecture and data model](docs/architecture.md) for the pipeline above
- [Qualification prompt patterns](docs/qualification-prompts.md) (channel-agnostic)
- [CRM field mapping examples](docs/crm-field-mapping.md)
- [Follow-up sequence patterns](docs/follow-up-patterns.md)
- [LICENSE](LICENSE)

## What stack does it work with?

The patterns are stack-agnostic, and the reference flow assumes tools most service businesses already have: n8n or Zapier for orchestration, an LLM for reply and qualification, your existing CRM and calendar. No platform lock-in: the value is the flow, not a single tool.

## How does this blueprint compare with building from scratch or buying a platform?

|  | This blueprint | Building from scratch | Closed all-in-one platform |
|---|---|---|---|
| Cost | Free (MIT); you pay only for the tools you run it on | No licence cost, but weeks of design and testing time | Monthly per-seat or per-contact subscription |
| Lock-in | None: the patterns live in your own stack | None, but the design knowledge stays in one person's head | High: flows, data and history stay in the vendor's system |
| Time to first workflow | Days: architecture, prompts and mappings are already designed | Weeks: every stage, edge case and prompt designed from zero | Hours to set up, but shaped around the vendor's model, not yours |
| Customisation | Full: every stage, field and message is yours to change | Full, at full design cost | Limited to the platform's options and integrations |

## Frequently asked questions

### What does AI Lead Automation cost?

Nothing. The blueprint is free and open source under the MIT license: read it, copy the patterns, and adapt them to your business. Your only costs are the tools you choose to run it on, such as an n8n or Zapier account, an LLM API, and the CRM and calendar you already use.

### Is AI Lead Automation software or a blueprint?

It is a blueprint and pattern library, not software you install. You get the architecture, qualification prompt patterns, CRM field mappings and follow-up sequences, then implement them in your own stack. If you want a runnable tool instead, LeadPipe MCP, TechAurah's open-source MCP server, covers the pipeline for businesses without a CRM.

### What stack does it work with?

The patterns are stack-agnostic. The reference flow assumes an automation platform such as n8n or Zapier for orchestration, a large language model for replies and qualification, and your existing CRM and calendar for records and booking. The CRM mapping examples cover HubSpot, Pipedrive, GoHighLevel and Google Sheets.

### Do I need to code to use it?

No, not for the common path. The blueprint can be implemented entirely with no-code and low-code tools: n8n or Zapier for the flow, your CRM's built-in fields, and the prompt patterns copied as written. Coding only helps when you outgrow templates and want custom scoring, integrations or self-hosted components.

### What does it not do?

It does not send messages, host anything, or store your leads: there is no product collecting your data. It is not a CRM replacement, an ad platform, or a guarantee of bookings. It covers lead handling after an inquiry arrives; generating the inquiries themselves is marketing, which stays your job.

### Can I use it for my clients?

Yes. The MIT license allows commercial use, including implementing the blueprint for paying clients, with no licence fee to TechAurah. Agencies can adapt the prompts, fields and sequences per client. Attribution is appreciated but not required beyond keeping the license notice with substantial copies of the material.

### How do I get help or report a problem?

Open a GitHub issue in this repository for errors, unclear sections or suggestions, and include the doc and step you were following. For implementation help or a done-for-you build, contact TechAurah through techaurah.com. Pattern contributions and corrections are welcome under the same issue-first route.

Questions and ideas: use [GitHub Discussions](https://github.com/techaurah/ai-lead-automation/discussions).

## More from TechAurah

- [LeadPipe MCP](https://github.com/techaurah/leadpipe-mcp): an MCP server giving businesses without a CRM a scored, bookable lead pipeline on Google Sheets and Calendar
- [n8n-audit](https://github.com/techaurah/n8n-audit): a production-readiness linter for n8n workflows, catching secrets, open webhooks and missing error handling
- [QualBench](https://github.com/techaurah/qualbench): outcome regression testing for AI qualification and booking agents, with mock CRM and calendar
- [ChaseKit](https://github.com/techaurah/chasekit): the open-source invoice-chasing layer, with statutory late-payment interest for the UK and EU
- [SlotFill](https://github.com/techaurah/slotfill): no-show recovery and waitlist backfill on the calendar a business already uses

## License

MIT. See [LICENSE](LICENSE). Businesses and builders are welcome to adapt the documentation and patterns in this repository for their own use.

---

TechAura · https://techaurah.com · Software. Intelligence. Automation.

## About TechAurah

TechAurah is an AI & Software Engineering company building AI products, agents, and intelligent automation for businesses in the USA, UK, UAE, Canada, Australia, and Europe.

We are available for AI engineering projects: https://techaurah.com

Follow TechAurah on [LinkedIn](https://www.linkedin.com/company/techaurah/).
