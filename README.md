# Victor Romanov

**Presales Solutions Architect: infrastructure, data center and enterprise AI**
Founder & AI Solution Architect of [TenderSRB](https://app.nab.rs) · Remote worldwide, open to relocation

[Website](https://victorromanovsite.github.io) · [LinkedIn](https://www.linkedin.com/in/romanovvictor/) · [Telegram](https://t.me/victorromanov_it) · victor.romanov.inbox@gmail.com

I design system architecture and drive it to a working product, and I lead the delivery, the vendors and the stakeholders around it.
25+ years in IT: built a bank's IT from scratch (core banking, card processing, 2 data centers, 10-minute RTO),
ran IT for a billing platform with 4M+ accounts, and delivered 93 projects with my own integration consultancy.
Today I build production AI systems: AI agents that write code under hard guardrails,
with every change proven by tests and live data before it ships.

**Open to:** Presales Solutions Architect · Solutions Consultant / Engineer · Proposal and Bid Solution Architect. Full-time, part-time or contract.

## TenderSRB: public tenders for the Western Balkans (case study)

**Live:** [app.nab.rs](https://app.nab.rs) · **News:** [t.me/nabrs_news](https://t.me/nabrs_news) · **Bot:** [@nabrs_bot](https://t.me/nabrs_bot) · **Company:** [LinkedIn](https://www.linkedin.com/company/tendersrb/)

A service that collects public tenders from Serbia and its neighbours, matches them to each client's profile,
and gives an AI go / no-go verdict before the client spends time on a bid.

As of 20 October 2026:

| | |
|---|---|
| Tenders processed | 60,500+ |
| Notifications delivered (Telegram, email) | 28,700+ |
| Live data sources | 7 (Serbian and Bosnian national portals, TED, EU delegations, World Bank and others) |
| Automated tests | 7,700+, all green before every merge |
| Architecture decisions recorded | 34 ADRs |

**What is inside**

- **Ingest:** adapters for national portals, TED, EU delegations, the World Bank; rate limits, robots.txt checks, a quiet first pass so a new source never floods clients.
- **Matching:** keywords in Latin and Cyrillic with one shared normaliser, a dictionary across Russian, English and Serbian, CPV codes, regions, budgets.
- **Delivery:** an outbox worker for Telegram and email, per-channel language, daily caps that the client can see.
- **AI layer:** go / no-go verdict, qualification checklist, deep analysis of tender documents; every paid model call has a tier limit, a gate before the call and a usage record after it.
- **Multi-tenant security:** PostgreSQL row-level security (`FORCE`), the app runs under a role that cannot bypass it; personal data never goes to logs.
- **Stack:** Python, FastAPI, SQLAlchemy 2, PostgreSQL, htmx, Docker, Caddy.

**How it is built**

One coordinator agent and worker agents (Claude Code) do the engineering. The coordinator never writes code:
it checks that a task has value in real data, writes the brief, reviews the pull request with a second agent,
runs the full test gate itself, merges and verifies the live site. A human (me) owns the decisions, the money and production data.

The public code: **[TnSrb1/nabrs](https://github.com/TnSrb1/nabrs)**: a snapshot of the private repository, translated to English.

More on the project: [TenderSRB case study](https://victorromanovsite.github.io/articles/tendersrb-case.html).
