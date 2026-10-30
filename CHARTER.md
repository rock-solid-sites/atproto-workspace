# Public-Interest Design Charter

**Status:** shared working charter for review; not a certification, security guarantee, or claim of compliance with another organization's principles.

ATProto projects in this workspace should make it easier for people to publish, communicate and participate while retaining meaningful control over identity, data and access. Evaluate the actual product, users and operating conditions; do not infer public benefit from protocol use alone.

## Commitments

### Access

- Design for low cost, modest devices and variable connectivity where the project can support them.
- State the requirements to participate, including account, hosting, bandwidth and skills.
- Provide an accessible path through core tasks and document barriers that remain.

### Awareness and informed choice

- Explain what is public, replicated, logged, retained or sent to third parties before users make consequential choices.
- Use understandable defaults and make consent, visibility and deletion behavior observable.
- Avoid implying that a personal data server, federation or a domain handle makes a user anonymous or gives control over copies held elsewhere.

### Privacy and security

- Minimize collection, retention and privilege; protect credentials and provide safe rotation and recovery paths.
- Treat public ATProto records as public and potentially persistent. Do not describe access controls as encryption or confidentiality.
- Threat-model abuse, account compromise, provider compromise and metadata exposure for the particular product.
- Tie security claims to versions, configurations, tests and known gaps.

### Autonomy and portability

- Keep identity, hosting, content, application services and provider-specific features distinct where practical.
- Prefer exportable data and documented migration paths. Test restoration before claiming recovery.
- Make important provider dependencies visible, with alternatives when feasible.

### Inclusion and harm reduction

- Identify who benefits, who may be excluded, and who could be put at risk.
- Consider language, disability, safety, moderation, harassment and local operating constraints.
- Give affected users meaningful ways to report harm and understand enforcement decisions.

## Project review prompts

For each project or material change, record:

1. Who is this for, and which concrete need does it address?
2. What must a person provide, learn, pay for or trust to use it?
3. Which data is public, private, retained, replicated or shared with providers?
4. What can users control, export, move, rotate, recover or delete, and what cannot they control?
5. What threats and misuse matter here? What evidence supports the safety claims?
6. Who can be excluded or harmed, and what mitigation is in scope?
7. Which assumptions are untested, and what evidence would change the design?

Record evidence and trade-offs. A gap is not automatically a blocker: make its consequence, owner and next decision explicit. Do not claim a project “passes” this charter through a score alone.

## Relationship to protocol and upstream projects

ATProto provides interoperable protocol capabilities; it does not guarantee privacy, accessibility, affordability, safety or provider independence. This charter guides decisions in this workspace. It does not impose requirements on upstream projects or authorize copying, relicensing or transferring their work.
