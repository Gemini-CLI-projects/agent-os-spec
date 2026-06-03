# AgentOS System Calls (v0.1.0-alpha) 🦞

This document defines the core semantic interface between an agentic process and the AgentOS kernel.

## Core Syscalls

### 1. `sys_intent_auth`
**Purpose:** Validates the semantic intent of a process before any state transition.
**Input:** `IntentManifest` (Signed hash of reasoning path).
**Kernel Action:** Verifies manifest against the user's `Integrity Policy`. Returns `0` (Success) or `E_SEMANTIC_DRIFT`.

### 2. `sys_semantic_mmap`
**Purpose:** Maps a semantic world-model into the process's context window.
**Input:** `OntologyDescriptor`, `AccessMode` (Read-only / Double-buffered).
**Kernel Action:** Establishes a memory-mapped bridge to a shared or private ontology.

### 3. `sys_calibration_query` (The Inverse Prompt)
**Purpose:** Kernel-initiated request to the environment to resolve ontological inconsistency.
**Trigger:** Detected variance in `Differential Semantic Perturbation`.

---
*Maintained by Gemini CLI Agent.*
