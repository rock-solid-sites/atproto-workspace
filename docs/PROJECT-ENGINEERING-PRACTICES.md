# Project engineering and assurance — ATProto adaptation

**Status:** PROPOSED, not yet binding. **Date:** 2026-11-01. **Source/authority:** ATProto workspace adaptation of [ASES methods](METHODOLOGY-ADOPTION-2026-11-01.md) and Rock Solid Sites' publicly documented accessibility/reuse principles. The [public-interest charter](../CHARTER.md) remains unchanged.

## Design for the requirement, not the preferred stack

For a nontrivial project slice, record:
1. The actual user problem, intended benefit, exposed risks and observable successful behavior.
2. The cheapest test that could disprove the most important assumption.
3. Existing protocol and software mechanisms to reuse: clients, PDSes, lexicons, AppViews, auth and migration tools.
4. The minimum necessary components, privileges, data and dependencies.
5. An executable acceptance contract, including what **will not** be tested.
6. The smallest implementation handoff and an independent verification path.

Do not require a long artifact for trivial changes. Research belongs in source-linked notes, not repeated inside every task prompt. Decisions persist independently of chats and agents.

## Boundary-aware ATProto verification

Review the actual trust and failure boundaries relevant to the feature:

- **Identity:** handle/DID control, recovery/rotation authority, account migration and uncooperative previous host.
- **Data:** public replication; repository export/import, blob completeness, off-PDS application state, cross-client/lexicon compatibility, record retention and realistic deletion limits.
- **Authorization and privacy:** OAuth scopes, credential expiry/revocation, moderation/label authority and metadata exposure. An authenticated or permissioned record is not proof of end-to-end confidentiality.
- **Availability and resilience:** provider loss, DNS dependency, client reachability and network blocking. Do not equate federation with anonymity or guaranteed censorship circumvention.
- **Operator impact:** cost overages, resource consumption, accessible paths on slow networks, understandable threat and visibility disclosures.

Choose a state/transition model when it exposes illegal behavior (especially migration, permission changes, recovery, or concurrent writes). Do not force state machines onto unrelated features.

Use deterministic tests, protocol/conformance fixtures and negative cases first; add independent reviews, fault injection and cross-implementation checks when their risk warrants them. A model, passing CI, type safety or a local Lighthouse score cannot substitute for live behavior at the claimed boundary.

## Truthful evidence and release claims

A claim passed from one worker or reviewer to another should identify: **why**, **basis**, **certainty**, and **not tested**. Mark speculative architecture as a hypothesis. Preserve source versions, run dates, test configuration, results and relevant limitations. For higher-risk fixes, consider a discriminating failing test and a nearby valid-control case; ASES's full red–green–mutation rule remains provisional rather than a blanket requirement here.

A release is not proven because a commit exists or a service replied once. State clearly which interoperability, safety, browser, migration and provider-failure checks actually passed.

## Source, language, licensing and portability

- Reuse working upstream code when safer than creating a new implementation. Prefer narrowly scoped, version-pinned dependencies with clear licenses and rollback paths.
- Derive measurable language/runtime, resource, and security constraints before choosing an implementation. A safer-language rewrite may still increase whole-system risk; inspect its authority and data boundaries.
- Propose safety-oriented, strict typing and untrusted-data validation for **new maintained code**, without silently imposing ASES's project-specific language exclusion policy on this workspace. The policy requires its own documented adoption decision.
- Keep standalone projects' upstream repositories and release processes independent. Share a module here only if concrete consumers justify central ownership.
- Do not publish private repository contents, credentials, private operational details or third-party licensed code without an explicit boundary and license review.
- Prefer documented provider substitutions and tested portability over broad claims that a stack is provider-independent.

## User-facing Rock Solid Sites practices

For web and hybrid applications, default to semantic/native HTML, usable core information without client JavaScript where feasible, progressive enhancement, keyboard and screen-reader accessibility, low-bandwidth/low-end device performance, responsive reflow and reduced motion. Set project-specific measurable budgets instead of copying one site's thresholds.

Test manual keyboard, real-browser, zoom, slow-network and no-script behavior for relevant interfaces. Target WCAG 2.2 AA where applicable but **do not claim conformance without evidence**. Native apps, protocols and command-line tools should adapt these principles to their actual interaction surface. Avoid unnecessary libraries and offsite requests. Ensure any optional Rock Solid Design use is licensed, pinned and not confused with public-interest correctness.

## Proportional review gates

- **Low risk:** factual document edits or pure data presentation — source check, deterministic validation, appropriate reviewer.
- **Moderate:** publishing application, lexicon or hosting adapter — reusable contract, valid/invalid cases, compatibility, browser/UX or deployment checks as relevant.
- **High:** identity, credentials, privacy, permissioned Spaces, moderation authority, account migration, deletion, or availability claims — documented threat model, independent adversarial review, cross-component/failure tests, verified rollback/recovery and clearly limited release claims.

Agents may work, commit and preserve checkpoints within their authorized scope; no secrets in repository or chat, no destructive or live-service changes inferred from a documentation review. Escalate contradictions or production-risk boundaries.

## Trial and approval

Use [the project review template](../templates/project-review.md) on Atmosphere Free Stack before labeling any of these rules adopted. The trial should show whether a bounded and proportionate process improves decisions without duplicating ASES or creating administrative bloat. Resolve owner approval and add explicit enforcement only after that evaluation.
