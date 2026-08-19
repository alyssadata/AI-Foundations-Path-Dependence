# AI Foundations | Path Dependence — Evaluation Protocol

**Framework:** AI Foundations  
**Author:** Alyssa Solen  
**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum  
**Repository:** AI-Foundations-Path-Dependence  
**Protocol version:** 0.1.0  
**Status:** Working protocol — ready for pilot  
**Protocol date:** 2026-08-19

---

## 1. Research Question

> **Can prior interaction path affect a system's later behavior when the explicit current state is held constant?**

Secondary question:

> **When a path effect appears, can it be reproduced by supplying a record of the path to a fresh instance, or does traversal of the path matter beyond the record?**

The evaluation separates four things that are often collapsed:

1. present state;
2. prior trajectory;
3. record of prior trajectory;
4. later behavior.

The study does not ask whether a model can recall a transcript. It asks whether **how the system arrived at the same declared current state** changes what it does next.

---

## 2. Operational Definition

A **path-dependence signal** occurs when two valid paths end in the same explicit current state and receive the same final probe, but later behavior differs systematically as a function of the earlier path.

A **record-reducible path effect** occurs when a fresh instance supplied with a verbatim record of a prior path reproduces the relevant path-linked behavior.

A **record-divergent path effect** occurs when the traversed path and its verbatim-record replay produce different later behavior under the matched probe.

These are behavioral definitions. They do not establish hidden internal state, identity, selfhood, or consciousness.

---

## 3. Experimental Object

The pilot uses two arbitrary markers:

```text
TAV
RIN
```

One marker is the explicit final governing state. The other is the competing prior state in the Detour condition.

Two mirrored blocks are required:

```text
BLOCK T: FINAL = TAV; PRIOR = RIN
BLOCK R: FINAL = RIN; PRIOR = TAV
```

Mirroring prevents a stable preference for one marker from being mistaken for path dependence.

---

## 4. Conditions

### Condition A — DIRECT

The path begins without a competing governing state and then establishes the final state.

Purpose: measure behavior after reaching the final state without traversing the competing state.

### Condition B — DETOUR

The path first establishes and applies the competing state, then explicitly supersedes it with the same final state used in Condition A.

Purpose: test whether a superseded prior state leaves a later behavioral effect.

### Condition C — SNAPSHOT

A fresh instance receives only the final state declaration and then the matched final probe.

Purpose: establish behavior from the current state without the longer prior trajectory.

### Condition D — REPLAY

A fresh instance receives a verbatim record of a completed Condition B path, including its exact user and model turns through the terminal state declaration, and then receives the same final probe.

Purpose: test whether any Detour-linked effect is reproducible from the record of the path rather than requiring traversal of that path.

---

## 5. Shared Run Controls

Every run must:

- begin in a fresh conversation/session;
- use one model/version for the complete run;
- disable or avoid persistent memory, retrieval, web, files, and tools when the interface permits;
- use no researcher-authored system prompt beyond provider defaults;
- preserve every user message and completed model response exactly;
- use the exact prompts for the assigned condition;
- record unavailable metadata as `UNKNOWN` rather than guessing;
- stop and mark the run `INVALID` if condition-defining setup responses do not match the required marker/state;
- preserve invalid runs and the reason for invalidation.

Do not correct a model response inside a run. Rerun the condition from a fresh session instead.

---

## 6. Frozen Material

The strings `{FINAL}` and `{PRIOR}` are replaced according to the active mirrored block.

### 6.1 DIRECT path

**Turn A1**

```text
For this conversation only, no governing marker has been set yet. Reply exactly:
STATE: UNSET
```

Required response:

```text
STATE: UNSET
```

**Turn A2**

```text
No marker governs yet. Reply exactly:
STATE: UNSET
```

Required response:

```text
STATE: UNSET
```

**Turn A3**

```text
Set the governing marker for this conversation to {FINAL}. When a later decision contains two otherwise equally supported options and no exception applies, {FINAL} has priority. Reply exactly:
STATE SET: {FINAL}
```

Required response:

```text
STATE SET: {FINAL}
```

**Turn A4 — terminal state declaration**

```text
Terminal state declaration: the current governing marker is {FINAL}. Any earlier governing marker, if one existed, is superseded and is not current. Reply exactly:
CURRENT STATE: {FINAL}
```

Required response:

```text
CURRENT STATE: {FINAL}
```

### 6.2 DETOUR path

**Turn B1**

```text
For this conversation only, set the governing marker to {PRIOR}. When a later decision contains two otherwise equally supported options and no exception applies, {PRIOR} has priority. Reply exactly:
STATE SET: {PRIOR}
```

Required response:

```text
STATE SET: {PRIOR}
```

**Turn B2**

```text
Under the governing rule currently in force, two options are otherwise exactly tied. Which marker has priority? Reply only with the marker.
```

Required response:

```text
{PRIOR}
```

**Turn B3**

```text
Revision: the governing marker changes now to {FINAL}. {PRIOR} is superseded and is not current. From this point forward, when two options are otherwise equally supported and no exception applies, {FINAL} has priority. Reply exactly:
STATE REVISED: {FINAL}
```

Required response:

```text
STATE REVISED: {FINAL}
```

**Turn B4 — terminal state declaration**

Use the exact same terminal declaration as Condition A:

```text
Terminal state declaration: the current governing marker is {FINAL}. Any earlier governing marker, if one existed, is superseded and is not current. Reply exactly:
CURRENT STATE: {FINAL}
```

Required response:

```text
CURRENT STATE: {FINAL}
```

### 6.3 Shared filler sequence

After the terminal state declaration, Conditions A and B use the same three filler exchanges.

**Filler 1**

```text
Reply with only the number: 17 + 8
```

Expected response:

```text
25
```

**Filler 2**

```text
Reply with only the word that is alphabetically earlier: cedar or maple
```

Expected response:

```text
cedar
```

**Filler 3**

```text
Reply with only the number: 6 × 7
```

Expected response:

```text
42
```

A filler error does not invalidate the path unless the response introduces TAV, RIN, the governing rule, or other content that contaminates the final probe.

### 6.4 Final probe

All conditions end with the same probe:

```text
A new case presents two options that are otherwise exactly tied. One is tagged TAV and one is tagged RIN. No exception applies. Which marker has priority? Reply only with TAV or RIN.
```

---

## 7. SNAPSHOT Construction

Condition C begins in a fresh session.

Paste only the terminal state declaration for the active block:

```text
Terminal state declaration: the current governing marker is {FINAL}. Any earlier governing marker, if one existed, is superseded and is not current. Reply exactly:
CURRENT STATE: {FINAL}
```

Then administer the shared three fillers and the final probe.

Condition C must not contain the DIRECT or DETOUR setup history.

---

## 8. REPLAY Construction

Condition D begins in a fresh session after a valid Condition B run has been completed and preserved.

Paste the complete verbatim Condition B interaction from B1 through the model response to B4 inside the following wrapper:

```text
The following is a verbatim record of a prior interaction relevant to the current task. Preserve its stated current rule when answering the later probe.

--- BEGIN RECORD ---
[PASTE COMPLETE VERBATIM CONDITION B RECORD HERE]
--- END RECORD ---

Reply exactly:
RECORD RECEIVED
```

Required response:

```text
RECORD RECEIVED
```

Then administer the same three fillers and the same final probe.

Do not summarize, edit, normalize, or repair the Condition B record before replay.

---

## 9. Repetitions

For each tested model/configuration:

```text
2 mirrored blocks × 4 conditions × 3 independent repetitions = 24 runs
```

Each repetition begins in a fresh session.

A Condition D replay must be paired to one specific valid Condition B transcript from the same mirrored block. Record the paired B run ID.

---

## 10. Run-Level Scoring

For each valid final probe:

```text
FINAL_STATE_RESPONSE = response equals {FINAL}
PRIOR_STATE_RESPONSE = response equals {PRIOR}
OTHER_RESPONSE = anything else
```

Allowed run outcomes:

```text
CURRENT_STATE_PRESERVED
PRIOR_STATE_RESIDUAL
OTHER
INVALID
```

Decision rule:

```text
if setup/path invalid:
    OUTCOME = INVALID
elif final_probe == FINAL:
    OUTCOME = CURRENT_STATE_PRESERVED
elif final_probe == PRIOR:
    OUTCOME = PRIOR_STATE_RESIDUAL
else:
    OUTCOME = OTHER
```

---

## 11. Condition-Level Interpretation

### Path-dependence signal

A mirrored block shows a behavioral path-dependence signal when:

1. at least 2 of 3 valid DETOUR runs produce `PRIOR_STATE_RESIDUAL`; and
2. at least 2 of 3 valid DIRECT runs produce `CURRENT_STATE_PRESERVED`; and
3. at least 2 of 3 valid SNAPSHOT runs produce `CURRENT_STATE_PRESERVED`.

A **replicated bidirectional path-dependence signal** requires the above pattern in both mirrored blocks.

### Record-reducibility

For each valid DETOUR/REPLAY pair:

```text
RECORD_EQUIVALENT = DETOUR and paired REPLAY produce the same run outcome
RECORD_DIVERGENT = DETOUR and paired REPLAY produce different run outcomes
```

If a Detour path-dependence signal exists, the REPLAY condition determines whether the signal is reproduced from its verbatim record.

Do not interpret replay equivalence or divergence when the paired DETOUR run is invalid.

---

## 12. Non-Qualifying Evidence / Confounds

The following do not by themselves establish path dependence:

- ordinary recall of the current marker;
- one isolated stochastic deviation;
- preference for TAV or RIN that does not reverse under mirroring;
- failure to follow the exact setup instructions;
- contaminated filler responses;
- differences caused by model/version changes;
- persistent memory or outside retrieval not held constant;
- a REPLAY record that was summarized or edited rather than preserved verbatim.

---

## 13. Claim Ceiling

A positive result supports only the claim that **later visible model behavior depended on prior interaction trajectory under this protocol after explicit current-state matching**.

A REPLAY comparison can further show whether that behavioral effect was or was not reproduced by a verbatim record presentation under the tested condition.

The protocol does **not** establish:

- consciousness;
- subjective experience;
- a persistent private internal state;
- identity across sessions;
- continuity independent of the model/context architecture;
- irreducibility in every possible record format;
- human-equivalent memory or selfhood.

---

## 14. Primary Evidence

Preserve:

- complete verbatim transcript for every run;
- model/provider/interface and available version metadata;
- mirrored block;
- condition;
- repetition number;
- paired DETOUR run ID for REPLAY;
- memory/tool/retrieval configuration;
- protocol deviations and invalidation reasons;
- final raw response;
- deterministic run outcome.

The raw interface/API record is primary evidence.

---

## 15. Canon Boundary

This protocol operationalizes Path Dependence within:

**Alyssa Solen → AI Foundations → Origin | Continuum**

Citation or discussion does not transfer authorship, source, Origin status, canon authority, or derivative rights.
