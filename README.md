# Cascade Dashboard V1.0

UI/UX storyboards for the **Cascade Enterprise Agent** — the browser-based, single-tenant agent workspace built by [Cascade Clarity](https://cascadeclarity.ai).

Nine user journeys and one system diagram, drawn on the Cowork interaction pattern, in the Cascade Clarity brand (Brand System Vol. 2), across two client tenants and two verticals. Every board is **tagged by the account it references** and shows the happy path **and** the error states beside it.

**▶ [View the storyboards](https://daveeedlr.github.io/Cascade-Dashboard-V1.0/)**

---

## Account tags

Every board carries a tag so it is clear which account it references:

- 🟦 **Cascade · Platform** — the system itself, applies to all tenants
- 🔵 **Construgypsum** — client tenant (Ecuadorian building-materials distributor, Odoo + WhatsApp)
- 🟣 **Huffmaster** — client tenant / Project Sword (US strike-staffing, Bullhorn + UKG + more)

## Contents

| | Board | Account | User | What it covers |
|---|---|---|---|---|
| — | [Global decision architecture](Cascade_Agents_Decision_Architecture.html) | Cascade · Platform | System-wide | The whole platform on one page: seven gates, each a yes/no decision, from connected system to real-world action |
| 01 | [Admin — steady state](Cascade_Enterprise_Agent_Storyboard.html) | Construgypsum | Administrator | Login, dashboard, connectors, chat surface, runs, run-detail approval gate |
| 02 | [Admin — onboarding](Cascade_Enterprise_Agent_Storyboard_02_Onboarding.html) | Construgypsum | Administrator, day one | Empty workspace, connecting Odoo, failed connection, permission scopes, roles, first run |
| 03 | [Operator — inventory](Cascade_Enterprise_Agent_Storyboard_03_Operator.html) | Construgypsum | Panchito, Chayabamba | WhatsApp digest entry point, stock-out to approved replenishment, weekly accuracy correction |
| 04 | [Executive — the business](Cascade_Enterprise_Agent_Storyboard_04_Executive.html) | Construgypsum | Francisco, Gerente General | Business dashboard, account 360, natural-language questions, weekly narrative, scope guard |
| 05 | [Field rep — WhatsApp only](Cascade_Enterprise_Agent_Storyboard_05_FieldRep.html) | Construgypsum | Luis, Vendedor | Visit prompt, free text parsed into a CRM record, no-reply branch, coaching nudge, privacy boundary |
| 06 | [Huffmaster — Project Sword](Cascade_Enterprise_Agent_Storyboard_06_Huffmaster.html) | Huffmaster | Trevor, Operations | Deployment view, hire-to-deploy orchestration, compliance gate, termination closing open spend, a different connector stack |
| 07 | [Sales manager — the team](Cascade_Enterprise_Agent_Storyboard_07_SalesManager.html) | Construgypsum | Andrea, Gerente Comercial | Team roster, coaching escalation from board 05, pipeline approval, collections, overruling an unfair flag |
| 08 | [Recruiter — order to recruit](Cascade_Enterprise_Agent_Storyboard_08_Recruiter.html) | Huffmaster | Marcus, Recruiter | Zoho→Bullhorn auto-fire, openings board, candidate kanban, 700-person surge projection, hand-off to hire-to-deploy |
| 09 | [Enterprise Reconciliation](Cascade_Enterprise_Agent_Storyboard_09_Reconciliation.html) | Cascade · Platform | Controller (new vertical) | Reconciliation dashboard, amount-mismatch with deterministic compute, missing-record, correcting-journal approval, audit trail |

Background reading: [Storyboard & Storybook primer](Storyboard_and_Storybook_Primer.md).

## Design notes

- **Single token layer.** Every board runs on the same CSS custom properties, derived from Brand System Vol. 2. Light and dark flip on one attribute, and re-skinning for a different client is a stylesheet swap rather than a rebuild.
- **Error states are drawn, not implied.** A storyboard that shows only the ideal path hides the moments the build actually has to get right.
- **Agents propose, humans approve.** No path in the architecture diagram reaches a write without passing the approval gate.
- **Self-contained.** Each HTML file opens standalone with no build step and no dependencies beyond web fonts.

## Status

`v1.0 · draft` — prepared by David De los Reyes for John Cuellar, July 2026. These are design artifacts, not an implemented application.
