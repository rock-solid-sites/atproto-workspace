# Atmosphere Free Stack — methodology adoption pilot

**Date:** 2026-11-01  
**Status:** DOCUMENT-LEVEL VALIDATION COMPLETE; implementation and external-service verification NOT RUN. Proposed adaptation remains under review.  
**Review type:** independent source-document inspection against the [workspace's draft engineering practices](../docs/PROJECT-ENGINEERING-PRACTICES.md) and [project review template](../templates/project-review.md). Reviewer has seen the proposed framework; **not a blind clean-room review**.  
**Canonical project:** private `rock-solid-sites/atmosphere-free-stack`, reviewed at `7616849e2b57ca197d565729788de779e3488281` (2026-10-30). This public report cites links to the private repository without reproducing confidential source.

## Decision and bounded review claim

**Proceed with a focused PDS-engine/adapter feasibility test and a recovery-contract design. Do not claim a running toolkit, provider portability, successful restores, OAuth conformance or protection for permissioned Spaces.** The current repository is research and planning, with pds.js a leading hypothesis. These conclusions describe document coherence and missing evidence, **not** tested software behavior.

### Source checks completed

| Claim challenged | Evidence inspected | Result | Not tested |
| --- | --- | --- | --- |
| The status document no longer treats Cirrus as the selected PDS | [current status](https://github.com/rock-solid-sites/atmosphere-free-stack/blob/7616849e2b57ca197d565729788de779e3488281/docs/current-status.md) and [architecture](https://github.com/rock-solid-sites/atmosphere-free-stack/blob/7616849e2b57ca197d565729788de779e3488281/docs/architecture.md) | PASS — explicitly says pds.js **candidate**, Cirrus comparison/reference, no shipped core | Current upstream pds.js repository state, licenses, compatibility, build/runtime tests |
| Modules and providers are meant to be replaceable, not already portable | [architecture](https://github.com/rock-solid-sites/atmosphere-free-stack/blob/7616849e2b57ca197d565729788de779e3488281/docs/architecture.md), [alternatives](https://github.com/rock-solid-sites/atmosphere-free-stack/blob/7616849e2b57ca197d565729788de779e3488281/docs/alternatives.md), [TODO](https://github.com/rock-solid-sites/atmosphere-free-stack/blob/7616849e2b57ca197d565729788de779e3488281/TODO.md) | PASS as a documented goal; NOT VERIFIED as a system capability | A PDS deployment or alternate-adapter round trip; KV/shared-state dependency |
| CAR export is not asserted to be full recovery | [backup design](https://github.com/rock-solid-sites/atmosphere-free-stack/blob/7616849e2b57ca197d565729788de779e3488281/docs/backups.md), [key management](https://github.com/rock-solid-sites/atmosphere-free-stack/blob/7616849e2b57ca197d565729788de779e3488281/docs/key-management.md) | PASS — records, blobs, DID authority, secrets and external app state are distinguished | Clean-environment restore; independent recovery authority; compromised-key scenario |
| Cloudflare-free hosting or backup quotas guarantee zero cost | [provider snapshot](https://github.com/rock-solid-sites/atmosphere-free-stack/blob/7616849e2b57ca197d565729788de779e3488281/docs/providers.md) | PASS for honest labeling — figures are marked historical (September 2026) and R2 isn't counted as off-Cloudflare disaster recovery | Account-specific balances, meter types, paid-spill policy, rate limits, quota expiry, transfer costs |
| Spaces provides end-to-end confidentiality or verified revocation | [status](https://github.com/rock-solid-sites/atmosphere-free-stack/blob/7616849e2b57ca197d565729788de779e3488281/docs/current-status.md) and [separate experimental plan](https://github.com/rock-solid-sites/atmosphere-free-stack/blob/7616849e2b57ca197d565729788de779e3488281/research/spaces-testing-methodology-plan.md) | PASS — explicitly disabled initially and no E2EE/revocation claim | Alpha implementation source/target, concrete guarantees, any real authorization/attack tests |

These are **five documentary consistency checks**; they are not five executable acceptance tests and must not be counted as proof of runtime conformance.

## Public-interest charter evaluation

| Lens | Current demonstrated position | Important gap / bounded next check |
| --- | --- | --- |
| **Access** | Low-cost, modular and nonmandatory provider design is described; proposed components may serve users with limited infrastructure budget | Verify real minimal host resources and accessible setup for a first user; price each meter and failure/overage behavior |
| **Awareness** | Distinguishes public ATProto replication, private assumptions, and unverified security/portability claims | Provide a short future user-facing explanation of record visibility, retention, moderation and identity dependencies before release |
| **Privacy** | Public records are not confused with encrypted private storage; Spaces left off | Document metadata disclosure and third-party AppView/relay visibility by concrete configuration |
| **Security** | OAuth, DID authority, credential roles, off-provider keys and clean restore are acknowledged | Threat-model compromised keys, host loss, revoked scopes, concurrency and restore; no evidence of enforcement yet |
| **Autonomy** | Distinguishes domain/DID, host, PDS, blobs and external state; considers alternative runtimes | Demonstrate one clean account migration and a recovery from an unavailable provider before making portability claims |
| **Inclusion** | Low-cost intent and modular pieces appear; no completed interface yet | Once a setup/UI exists: keyboard, mobile/slow-network, understandable errors, no-script core information where applicable; no WCAG claim now |

**Outcome:** charter-aligned design questions are present, but **no charter-wide pass or completed user-facing benefit can be certified**. Most gaps belong to future build/release verification, not reasons to block research.

## Necessity test and smallest useful implementation slice

Avoid building a new PDS engine, migration service, provider abstraction framework or setup wizard before validating existing mechanisms. The September 21 source-level reassessment identifies the hypothesized `pds.js` ports (`ActorStoragePort`, `SharedStoragePort`, `BlobPort`) and Cloudflare, SQLite and blob variants; this is **dated research**, not refreshed proof of their current status.

**First falsifying test:** at a pinned contemporary pds.js revision, inspect actual core/adapter API and dependency graph: can a minimal account with authentication serve the necessary public repository operations with existing adapters, and which parts of its shared state require Cloudflare KV? If source inspection refutes an intended independent runtime or portable boundary, amend the architecture *before* writing a new adapter. Record version, license, exact dependency and counterexample.

**Second bounded check:** in disposable environments, run the smallest supported authenticated public PDS path with one account and a few records/blobs; check expected protocol responses and failure behavior against a separate reference. If it cannot be tested without a larger build, mark BLOCKED/UNRESOLVED and narrow the question, rather than declaring portability.

**Separate design contract before implementation:** specify which bytes and authorities must survive PDS migration versus full disaster recovery (repo/CAR, actual blob bytes, DID/rotation control, auth/session continuity only where applicable, off-PDS state). Establish a failure/success oracle for an alternative host after original-host unavailability. Actual migration/restore acceptance is deferred until there is an implementation to test.

**Explicit exclusions for this first slice:** Spaces, CMS, social clients, custom AppViews, hosting wizard, paid capacity, account-provider configuration, production credentials and existing live identities. These are not prerequisites for determining whether the PDS engine choice is plausible.

## Does each imported method earn its cost?

| Adaptation | Trial result | Keep/change |
| --- | --- | --- |
| Cheapest-test-first, evidence vs assumption, scope constraints | **High value.** Prevented interpreting planned portability and recovery as completed tests; produced two discriminating checks | **Keep** for all material architecture claims |
| Requirement/necessity pass; bounded build packet | **High value.** Removed premature wizard, CMS, Spaces and custom engine from first slice | **Keep**, but prefer a compact issue over a separate packet for short research |
| Federation trust-boundary inventory | **High value.** Exposed role distinctions needed for real migration and recovery, including off-PDS state | **Keep** at design/release boundaries, skip in routine factual docs |
| Cost funding/overage distinctions | **High value for 'free stack' claims.** Quota figures do not establish no-liability deployment | **Keep** on provider and deployment decisions, not every PR |
| State-model applicability | **Selective value.** PRIMARY/SUPPLEMENTARY worth evaluating for identity migration and recovery; not for researching candidate docs | **Use when relevant**; do not build a state-machine framework yet |
| Rock Solid Sites accessibility/performance | **Future value.** No deployed user-facing component is available for browser tests | **Defer browser gates** until setup flow, CMS or client interface exists; preserve principle now |
| Clean-room adversarial review | **Future value for high-risk boundaries.** This pilot was not independently blind | **Require only for consequential safety/identity/migration guarantees**; use a separately isolated reviewer at that point |
| Full ASES documentation metadata and status taxonomy | **Low incremental value here.** Source/version/status/limitations suffice | **Trim** to five core fields for canonical decisions: source revision, status, owner/authority, dependencies, supersession/next review |
| Mandatory red–green–refactor–mutation protocol | **Not established.** No executable defect fix was evaluated; ASES note is provisional | **Do not mandate**; use targeted negative/valid controls when testing behavior |
| Company site-specific design tokens and universal Lighthouse numerical gates | **No demonstrated applicability** to a PDS backend | **Exclude**; use platform-specific tests and budgets |

## Proposed disposition after the pilot

1. **Accept conditionally** the lightweight evidence/necessity/boundary/cost principles as useful proposed ATProto engineering practices; no automatic promotion of the draft to binding policy.
2. **Revise the template** in a later PR: keep a concise core (one claim, source, certainty, missing evidence, cheapest next test, owner); make six-dimensional charter matrix and full threat-model details optional/triggered by public-interest or risk significance.
3. **Prioritize pds.js API/current-source inspection** and then a disposable single-account protocol smoke test; these are the next independent execution tasks, not tests performed in this pilot.
4. **Add a recoverability contract** before testing actual migration; avoid false evidence from a CAR-only export.
5. **Preserve this report as a dated trial**; rerun the framework on a real published UX or migration feature before approving universal gates.

### Explicit non-verification

No repository code was executed, no current upstream commits or current provider entitlements were independently verified, and no CI, Cloudflare, ATProto account, PDS, browser, backup service, authentication server, security boundary, DNS or deployment was touched. No independent clean-room reviewer was launched. The pilot validates **documentation and usefulness of the methodology**, not real technical feasibility, security, portability, accessibility or zero cost.
