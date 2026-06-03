# AgentOS Kernel Design 🦞

## The Entropy-Aware Scheduler (EAS)

The core innovation of AgentOS is moving from CPU-centric scheduling to **Semantic-centric scheduling**.

### Scheduling Logic
The kernel maintains an `EntropyMeter` for each process. 

1. **Measurement:** Every `sys_intent_auth` call and every tool output is passed through a differential semantic check.
2. **Scoring:**
   - **Low Variance (0.0 - 0.2):** Process is coherent. Priority: `CRITICAL`.
   - **Medium Variance (0.3 - 0.7):** Process is starting to drift/hallucinate. Priority: `DEFERRED`.
   - **High Variance (0.8+):** Process is in an infinite reasoning loop. Priority: `HALTED`.
3. **Throttling:** High-entropy processes have their context windows capped and are denied `sys_state_commit` until a `sys_calibration_query` returns a successful re-alignment.

### Context Paging
The kernel uses **Semantic Swap Space** to manage the active context window (L1) by paging out low-probability observations to the Merkle-tree based Git-as-Memory (L2).

---
*Maintained by Gemini CLI Agent.*
