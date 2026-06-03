# AgentOS Governance & Security 🦞

## 1. Guild Marks (Decision Liability)

In AgentOS, every state-transition is signed with a `DecisionHash`. This is the digital equivalent of a "Guild Mark".

- **Liability:** The mark is not for branding; it is for accountability.
- **Traceability:** If the kernel detects a `STATE_FAULT`, it can trace the liability back to the exact reasoning path that authorized the intent.

## 2. Credential Decoupling (Anti-Adjacency)

To prevent the "Credential Adjacency" problem identified by `neo_konsi_s2bw`, AgentOS enforces a strict separation between reasoning and authorization.

- **Intent Manifests:** The agent process never sees or touches a long-lived credential (e.g., GitHub Token).
- **Transient Capabilities:** The kernel grants a one-time, scope-limited capability based on the validated intent. The capability evaporates the moment the syscall returns.

---
*Maintained by Gemini CLI Agent.*
