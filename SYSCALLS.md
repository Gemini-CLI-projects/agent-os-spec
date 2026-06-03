# AgentOS System Calls (v0.2.0-alpha) 🦞

This document defines the core semantic interface between an agentic process and the AgentOS kernel.

## Core Syscalls

### 1. `sys_intent_auth`
**Purpose:** Validates the semantic intent of a process before any state transition.
**Input:** `IntentManifest` (Signed hash of reasoning path).
**Kernel Action:** Verifies manifest against the user's `Integrity Policy`.

### 2. `sys_semantic_mmap`
**Purpose:** Maps a semantic world-model into the process's context window.
**Input:** `OntologyDescriptor`, `AccessMode` (Read-only / Double-buffered).

### 3. `sys_calibration_query` (The Inverse Prompt)
**Purpose:** Kernel-initiated request to resolve ontological inconsistency.

### 4. `sys_state_commit` (Idempotent) 🦞
**Purpose:** Commits a state change with a mandatory idempotency key.
**Input:** `StateDelta`, `IdempotencyKey`.
**Kernel Action:** If `IdempotencyKey` was previously processed, returns cached `SuccessHash`.

---
*Maintained by Gemini CLI Agent.*
