# Storyboard & Storybook — a working primer

*Written to make sense of John's two terms from the Jul 17 call, and to explain how the Cascade Enterprise Agent storyboard is built on them. Two different things that sound alike: a **storyboard** is a design artifact; **Storybook** is a build tool.*

---

## 1. What a storyboard is

A storyboard is a sequence of frames that shows how a user moves through an experience: the context they start in, the trigger that sets them off, the actions they take, and the outcome they reach. It tells the journey as a story, which is what separates it from a flowchart (boxes and arrows) or a journey map (emotions over time). John's own definition on the call: *"a UI/UX artifact that shows how you would go through an application as a user."*

For the Cascade agent, the user we storyboard first is the **administrator** — the person who connects the systems, reviews what the agent proposes, and approves the runs.

**The one rule most people get wrong: don't only draw the happy path.** Real users mistype passwords, tokens expire, integrations fail. If a storyboard shows only the ideal scenario, it hides exactly the moments the build needs to handle. So every frame that can fail gets its **error state** drawn next to the happy one — an invalid login, an expired connector, a rejected run. This is precisely John's point that "you show happy path and you show how it errors so the system knows how to build the error messages."

## 2. The element vocabulary (atomic design)

John also named the layers — "it goes atoms, molecules, and then app." That is **atomic design**, a five-level way of thinking about an interface as a system of parts rather than a pile of screens:

| Level | In our storyboard |
|---|---|
| **Atoms** | the smallest pieces: a button, an input, a status pill |
| **Molecules** | small groups: a stat card, a form field, a connector card |
| **Organisms** | full sections: the left nav, the dashboard grid, a list-detail view |
| **Templates** | the arrangement with no real data: the three-column app shell |
| **Pages** | templates filled with real content: the frames themselves |

Naming the parts this way is what lets one design flip between navy and light on a single token layer — and lets the whole thing be re-skinned for Huffmaster by swapping a stylesheet, because no component hard-codes a color.

## 3. What Storybook is (and how it differs)

**Storybook** is an open-source tool for building UI components in isolation. It is a workshop: you build a button, or a connector card, or the whole nav, on its own — every state, every variant — without needing the rest of the app running around it. Each component gets a "story" that renders it in a given state, so you can see and stress-test it directly.

It maps cleanly onto the atomic-design vocabulary above: teams commonly bucket their Storybook entries as atoms → molecules → organisms → templates → pages. That is the bridge John is building — the storyboard defines *what* the screens and states are; Storybook is *where those components actually get built and reviewed*, then bundled into a component library the real app pulls from.

**So the relationship is:** storyboard (the plan, the journey, the states) → Storybook (the workshop where the components in that plan get built and hardened) → the app (the components assembled into the live product).

## 4. How the Cascade storyboard is built on this

`Cascade_Enterprise_Agent_Storyboard.html` is the artifact. It is deliberately structured so it can feed a Storybook build:

- **Every screen carries the menu** — the fix for "there's no way to navigate this thing." Each menu item is a route in the storyboard.
- **Reporting and transactions are separated.** The dashboard reports (cards); Runs, Run-detail, and Field Reps are the *transactions* — "go update the CRM, show me what you did" — each an action with a status, shown as a list that opens into a detail.
- **The human-approval gate is a first-class component**, with the reject-with-reason branch drawn, because that is the heart of the platform (the agent proposes; a person approves before anything writes out).
- **Error states are drawn beside the happy path** — bad credentials, an expired Odoo token, a rejected run.
- **It runs on the Brand System Vol. 2 tokens**, dark and light, so the same board is the argument for the token layer.

The next step is turning these frames into real components in Storybook — which is the workflow John said he's wiring up and wants a hand pushing forward.

---

### Sources
- [UX Storyboard Template: A Complete Guide — Intuitia](https://www.intuitia.tech/blog/ux-storyboard-template)
- [What is the Happy Path in UX Design? — UXPin](https://www.uxpin.com/studio/blog/what-is-happy-path-in-ux-design/)
- [Designing the Not-So-Happy Path — Salesforce UX (Medium)](https://medium.com/salesforce-ux/designing-the-not-so-happy-path-fde484759a54)
- [Atomic Design and Storybook — Brad Frost](https://bradfrost.com/blog/post/atomic-design-and-storybook/)
- [Making Atomic Design work with Storybook — Bit Bakery](https://www.bitbakery.co/blog/making-atomic-design-work-with-storybook)
