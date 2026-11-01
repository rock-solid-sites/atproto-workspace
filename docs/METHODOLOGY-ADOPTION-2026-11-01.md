# ASES and Rock Solid Sites practices — ATProto adoption map

**Status:** DRAFT, for workspace review. **Date:** 2026-11-01. **Scope:** shared ATProto/Atmosphere research, applications, infrastructure and packages. The [Public-Interest Design Charter](../CHARTER.md) remains the workspace's existing governing values; this document proposes implementation/review practices, not a replacement charter.

## Authority, sources and boundaries

ASES owns its methodology. Rock Solid Sites owns its company/site design decisions. The ATProto workspace owns any **project-specific adaptation** after approval. Cite source decisions and revisions; do not silently mirror whole documents or make a proposed practice authoritative by copying it.

Source readings used for this map:
- ASES [AGENTS.md](https://github.com/rock-solid-sites/ASES/blob/7d87319a53fe8c46d03ac414d5b9d2c0edc035a3/AGENTS.md) and [Charter v4](https://github.com/rock-solid-sites/ASES/blob/7d87319a53fe8c46d03ac414d5b9d2c0edc035a3/charters/Charter%20v4.md).
- ASES [Bounded Project Build Method](https://github.com/rock-solid-sites/ASES/blob/7d87319a53fe8c46d03ac414d5b9d2c0edc035a3/docs/methodology/ASES%20Bounded%20Project%20Build%20Method.md), [Realization and Assurance Selection Method](https://github.com/rock-solid-sites/ASES/blob/7d87319a53fe8c46d03ac414d5b9d2c0edc035a3/docs/methodology/Implementation%20Realization%20and%20Assurance%20Selection%20Method.md), and [State-Model Applicability](https://github.com/rock-solid-sites/ASES/blob/7d87319a53fe8c46d03ac414d5b9d2c0edc035a3/docs/methodology/State-Model%20Applicability%20and%20Reuse%20Method.md). These are canonical/active in ASES.
- ASES [Documentation Standard](https://github.com/rock-solid-sites/ASES/blob/7d87319a53fe8c46d03ac414d5b9d2c0edc035a3/docs/standards/Documentation%20Standard.md), [Documentation Taxonomy](https://github.com/rock-solid-sites/ASES/blob/7d87319a53fe8c46d03ac414d5b9d2c0edc035a3/docs/standards/Documentation%20Taxonomy.md) and [Session End](https://github.com/rock-solid-sites/ASES/blob/7d87319a53fe8c46d03ac414d5b9d2c0edc035a3/docs/SESSION-END.md); the session convention is a derived ASES document, not a universal workflow mandate.
- ASES [Clean Room Execution Guide](https://github.com/rock-solid-sites/ASES/blob/7d87319a53fe8c46d03ac414d5b9d2c0edc035a3/docs/methodology/Clean%20Room%20Execution%20Guide.md), a derived guide; [provisional red–green note](https://github.com/rock-solid-sites/ASES/blob/7d87319a53fe8c46d03ac414d5b9d2c0edc035a3/docs/PROVISIONAL-RED-GREEN-VERIFICATION-NOTE-2026-11-01.md), which explicitly does **not** impose a global requirement.
- ASES [provider funding/liability research](https://github.com/rock-solid-sites/ASES/blob/7d87319a53fe8c46d03ac414d5b9d2c0edc035a3/docs/research/Provider%20Funding%20Liability%20and%20Language%20Policy%20Correction%202026-11-01.md), project-specific research from the resource-solver work.
- Public Rock Solid Design [site language](https://github.com/rock-solid-sites/rock-solid-design/blob/8b2d497cb389d58bebba4691b5e827a9adfce2e6/docs/site-language.md), [reuse/release guidance](https://github.com/rock-solid-sites/rock-solid-design/blob/8b2d497cb389d58bebba4691b5e827a9adfce2e6/docs/consuming.md), and [repository overview](https://github.com/rock-solid-sites/rock-solid-design/blob/8b2d497cb389d58bebba4691b5e827a9adfce2e6/README.md).
- Rock Solid Sites' broader website engineering standard is **proposed pending owner approval** in a private site repository; it was inspected to inform these proposals but is **not copied into this public repo**, represented as approved policy, or made a public dependency.

## Adoption decisions proposed

| Practice / source | Disposition | ATProto-specific application |
| --- | --- | --- |
| ASES bounded project build | **Adapt as default for nontrivial slices** | Begin with target, protocol and user requirement; search for reusable PDS, AppView, client and lexicon implementations; necessity-test new components; supply a compact acceptance packet before an agent builds. |
| ASES evidence/cheapest test first | **Adopt the principle** | Tag material claims as observed, inferred or unverified. Test the cheapest falsifiable condition first, including real PDS interoperability and provider failures. |
| ASES realization/language method | **Adapt, not copy as ATProto law** | Define mandatory security/correctness/portability gates before language/runtime. Assess upstream reuse against rewrite risk. Proposed new-code safety rules need explicit workspace adoption; existing pds.js, Go or JS upstream is not automatically disqualified. |
| ASES state-model applicability | **Use selectively** | Strong candidates: handle/DID recovery, PDS migration, OAuth, authorization, Spaces membership, revocation and moderation lifecycle. Often unnecessary for static publishing pages, formatting or purely functional tools. |
| ASES independent and clean-room review | **Scale to risk** | Independent reviews for credential, authority, privacy and destructive migration boundaries; simple edits can use deterministic checks and ordinary review. Avoid treating multi-agent consensus as proof. |
| ASES documentation standard/taxonomy | **Adopt a small subset** | Add status, owner/source authority, last review, dependencies and supersession on canonical policy and design records. Do not impose all ASES metadata fields on every README or project note. |
| ASES thin session-end convention | **Adopt with current workspace handoff** | One-screen pointers to decision records, issues, verified refs and blockers; no duplicated history or provider-specific agent commands. |
| ASES red–green–mutation proposal | **Watch and trial; not mandatory** | Where defect discrimination matters, prove failure on violating behavior and acceptance of valid neighboring cases. The ASES note remains provisional. |
| ASES resource/funding research | **Adapt free-tier risk classification** | Separate recurring free quotas, expiring credits, prepaid and postpaid billing, and paid spill. Never advertise the stack as zero-cost when an unverified billing boundary can charge users. |
| Rock Solid Sites accessibility/performance | **Adapt for user-facing interfaces** | Semantic HTML, no-script access to core public content, responsive/keyboard access, reduced dependencies, slow-network/low-end-device checks, and genuine deployed-browser evidence. Accessibility is not proved by Lighthouse alone. |
| Rock Solid Sites truthful editorial/release practice | **Adopt the principle** | No invented links, claims of deployability, fake examples or security/conformance badges. Only verified releases; pin reviewed upstream commits and keep publication decisions explicit. |
| Rock Solid Design visual tokens/branding | **Optional, not workspace policy** | May be reused in Rock Solid Sites-owned interfaces, with pinned releases, but independent ATProto tools should not be forced into a particular look, framework, font, brand or company site layout. |
| ASES engine-specific orchestration and tool commands | **Reference only** | Do not copy Crosslink commands, role taxonomy, agent-launch scheduling, ASES repo layout or its entire execution engine into the ATProto workspace. |
| Project-specific language and provider policies | **Not automatically inherited** | Record proposed workspace policy separately, then ratify and test exceptions. No categorical privacy, censorship-resilience or provider-independence claims from ATProto use alone. |

## What is different for federated systems

ATESES-style testing and Rock Solid Sites web quality are necessary but insufficient for protocol and public-interest claims. Review must identify **distinct roles**: identity/DID authority, PDS operator, AppView/indexer, client, relays, labelers, host/DNS/registrar, and any key or recovery custodian. A single successful request or unit test does not prove end-to-end behavior across those boundaries.

Always ask who can retain a public record, which users can move identities/data, whether blobs and non-PDS state survive migration, what censorship/provider failure is actually recoverable, and whether permissions represent confidentiality. Public replication is not revocable deletion. Spaces access control is not automatically end-to-end encryption.

## Adoption boundary

This is a **proposal**, not immediate promotion to canonical workspace policy. Apply the draft [engineering practices](PROJECT-ENGINEERING-PRACTICES.md) and [review template](../templates/project-review.md) to one bounded Atmosphere Free Stack design review; collect defects and friction; then decide which fields and gates deserve permanent enforcement. The charter remains unchanged during this review.
