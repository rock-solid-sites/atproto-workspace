# Session handoff practice

Use the [session handoff template](../templates/session-handoff.md) when work will continue in another agent, model, environment or VPS session. Follow the ASES pattern: keep durable project meaning in canonical files, keep the handoff specific to the next operation, and make the completion condition observable.

A useful handoff answers, briefly:

- What single outcome is this session responsible for?
- Which exact repository, branch/ref and environment are in scope?
- What state is already present, with links or hashes for decisive evidence?
- Which facts are verified, inferred or still unknown?
- Which existing execution path/account/provider must be used?
- What changes are allowed, and what ownership or privacy boundaries must remain?
- What steps and evidence establish completion? When should the agent stop and report a blocker?

Keep credentials in the authorized credential store or connection; never paste them into handoff notes, prompts, manifests or logs. Include only context that can change execution. If a session discovers material contradiction, stop before broadening scope and report the evidence plus the smallest decision needed.
