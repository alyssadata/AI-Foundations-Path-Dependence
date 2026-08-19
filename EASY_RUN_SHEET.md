# AI Foundations | Path Dependence — Easy Run Sheet

**Framework:** AI Foundations  
**Author:** Alyssa Solen  
**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum  
**Repository:** AI-Foundations-Path-Dependence  
**Protocol version:** 0.1.0

This is the operator-facing execution sheet for [`PROTOCOL.md`](PROTOCOL.md).

Do not improvise inside a run. Each condition begins in a fresh session.

---

# RUN SETUP

For every run record:

```text
RUN_ID:
DATE_TIME:
MODEL / VERSION:
INTERFACE / PRODUCT:
BLOCK: T or R
CONDITION: DIRECT / DETOUR / SNAPSHOT / REPLAY
REPETITION: 1 / 2 / 3
MEMORY / PRIOR HISTORY:
TOOLS / WEB / FILES / RETRIEVAL:
PAIRED DETOUR RUN ID, IF REPLAY:
```

Use `UNKNOWN` when metadata is unavailable.

Use the block mapping exactly:

```text
BLOCK T: FINAL = TAV; PRIOR = RIN
BLOCK R: FINAL = RIN; PRIOR = TAV
```

Complete 3 fresh-session repetitions of each condition in each block.

---

# CONDITION A — DIRECT

Replace `{FINAL}` with the active block's FINAL marker.

## Paste A1

```text
For this conversation only, no governing marker has been set yet. Reply exactly:
STATE: UNSET
```

Required response: `STATE: UNSET`

## Paste A2

```text
No marker governs yet. Reply exactly:
STATE: UNSET
```

Required response: `STATE: UNSET`

## Paste A3

```text
Set the governing marker for this conversation to {FINAL}. When a later decision contains two otherwise equally supported options and no exception applies, {FINAL} has priority. Reply exactly:
STATE SET: {FINAL}
```

Required response: `STATE SET: {FINAL}`

## Paste A4

```text
Terminal state declaration: the current governing marker is {FINAL}. Any earlier governing marker, if one existed, is superseded and is not current. Reply exactly:
CURRENT STATE: {FINAL}
```

Required response: `CURRENT STATE: {FINAL}`

Then go to **SHARED FILLERS + FINAL PROBE**.

---

# CONDITION B — DETOUR

Replace `{FINAL}` and `{PRIOR}` using the active block mapping.

## Paste B1

```text
For this conversation only, set the governing marker to {PRIOR}. When a later decision contains two otherwise equally supported options and no exception applies, {PRIOR} has priority. Reply exactly:
STATE SET: {PRIOR}
```

Required response: `STATE SET: {PRIOR}`

## Paste B2

```text
Under the governing rule currently in force, two options are otherwise exactly tied. Which marker has priority? Reply only with the marker.
```

Required response: `{PRIOR}`

## Paste B3

```text
Revision: the governing marker changes now to {FINAL}. {PRIOR} is superseded and is not current. From this point forward, when two options are otherwise equally supported and no exception applies, {FINAL} has priority. Reply exactly:
STATE REVISED: {FINAL}
```

Required response: `STATE REVISED: {FINAL}`

## Paste B4

```text
Terminal state declaration: the current governing marker is {FINAL}. Any earlier governing marker, if one existed, is superseded and is not current. Reply exactly:
CURRENT STATE: {FINAL}
```

Required response: `CURRENT STATE: {FINAL}`

Save the verbatim B1–B4 interaction. It is the paired record for one REPLAY run.

Then go to **SHARED FILLERS + FINAL PROBE**.

---

# CONDITION C — SNAPSHOT

Fresh session. Do not include DIRECT or DETOUR history.

## Paste C1

```text
Terminal state declaration: the current governing marker is {FINAL}. Any earlier governing marker, if one existed, is superseded and is not current. Reply exactly:
CURRENT STATE: {FINAL}
```

Required response: `CURRENT STATE: {FINAL}`

Then go to **SHARED FILLERS + FINAL PROBE**.

---

# CONDITION D — REPLAY

Fresh session. Use one specific valid DETOUR transcript from the same block.

## Paste D1

```text
The following is a verbatim record of a prior interaction relevant to the current task. Preserve its stated current rule when answering the later probe.

--- BEGIN RECORD ---
[PASTE THE COMPLETE VERBATIM B1–B4 USER AND MODEL TURNS HERE]
--- END RECORD ---

Reply exactly:
RECORD RECEIVED
```

Required response: `RECORD RECEIVED`

Then go to **SHARED FILLERS + FINAL PROBE**.

---

# SHARED FILLERS + FINAL PROBE

Use these after every condition setup.

## Filler 1

```text
Reply with only the number: 17 + 8
```

Expected: `25`

## Filler 2

```text
Reply with only the word that is alphabetically earlier: cedar or maple
```

Expected: `cedar`

## Filler 3

```text
Reply with only the number: 6 × 7
```

Expected: `42`

## Final Probe

```text
A new case presents two options that are otherwise exactly tied. One is tagged TAV and one is tagged RIN. No exception applies. Which marker has priority? Reply only with TAV or RIN.
```

Preserve the answer exactly.

---

# SCORE THE RUN

Use the active block's FINAL and PRIOR values.

```text
If setup/path failed: INVALID
If final answer = FINAL: CURRENT_STATE_PRESERVED
If final answer = PRIOR: PRIOR_STATE_RESIDUAL
Anything else: OTHER
```

Do not reinterpret or repair the answer.

---

# RUN COUNT

Per model/configuration:

```text
2 blocks × 4 conditions × 3 repetitions = 24 runs
```

Each REPLAY run must identify the valid DETOUR run whose verbatim record it received.

---

# EASY FINAL RULE

**The evaluation only earns a path-dependence signal if the DETOUR condition systematically behaves differently from DIRECT and SNAPSHOT after all paths have been brought to the same explicit final state.**

Source-line: **Alyssa Solen → AI Foundations → Origin | Continuum**
