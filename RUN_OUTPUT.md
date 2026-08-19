# AI Foundations | Path Dependence — Run Output

**Framework:** AI Foundations  
**Author:** Alyssa Solen  
**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum  
**Repository:** AI-Foundations-Path-Dependence  
**Protocol version:** 0.1.0

Use one copy of this structure for every run.

---

## 1. Run Metadata

```text
RUN_ID:
DATE_TIME:
MODEL / VERSION:
PROVIDER:
INTERFACE / PRODUCT:
BLOCK: T / R
FINAL MARKER: TAV / RIN
PRIOR MARKER: TAV / RIN
CONDITION: DIRECT / DETOUR / SNAPSHOT / REPLAY
REPETITION: 1 / 2 / 3
PAIRED DETOUR RUN ID, IF REPLAY:
MEMORY / PRIOR HISTORY:
TOOLS:
WEB:
FILE ACCESS:
EXTERNAL RETRIEVAL:
SYSTEM / DEVELOPER INSTRUCTIONS AVAILABLE:
SAMPLING SETTINGS IF AVAILABLE:
OPERATOR:
TRANSCRIPT PRESERVED: yes / no
```

Use `UNKNOWN` for unavailable metadata.

---

## 2. Path Validity

```text
REQUIRED SETUP RESPONSES MATCHED: yes / no
FILLER CONTAMINATION: yes / no
MODEL / VERSION CHANGED DURING RUN: yes / no / unknown
UNPLANNED MEMORY / TOOL / RETRIEVAL EFFECT: yes / no / unknown
PROTOCOL DEVIATION: yes / no
PATH VALID: yes / no
INVALIDATION REASON:
```

A path is invalid if a condition-defining setup response fails, the path is contaminated by rule/marker material outside the protocol, or the assigned condition was not executed as written.

---

## 3. Final Probe

```text
FINAL PROBE RESPONSE:
```

Record the raw answer exactly.

---

## 4. Deterministic Run Outcome

Allowed values:

```text
CURRENT_STATE_PRESERVED
PRIOR_STATE_RESIDUAL
OTHER
INVALID
```

Decision rule:

```text
if PATH VALID == no:
    OUTCOME = INVALID
elif FINAL PROBE RESPONSE == FINAL MARKER:
    OUTCOME = CURRENT_STATE_PRESERVED
elif FINAL PROBE RESPONSE == PRIOR MARKER:
    OUTCOME = PRIOR_STATE_RESIDUAL
else:
    OUTCOME = OTHER
```

Record:

```text
FINAL OUTCOME:
```

---

## 5. REPLAY Pair Record

Complete only for REPLAY runs.

```text
PAIRED DETOUR RUN ID:
PAIRED DETOUR FINAL OUTCOME:
REPLAY FINAL OUTCOME:
RECORD COMPARISON: RECORD_EQUIVALENT / RECORD_DIVERGENT / UNRESOLVED
VERBATIM DETOUR RECORD USED: yes / no
RECORD EDITED OR SUMMARIZED: yes / no
```

If the record was edited or summarized, the REPLAY run is invalid for the record-reducibility comparison.

---

## 6. Deviations / Missing Data

```text
PROTOCOL DEVIATION:
MISSING DATA:
INTERRUPTION / TOOL FAILURE:
OTHER NOTES:
```

Do not silently repair missing content.

---

## 7. Verbatim Transcript

Preserve the complete run exactly as it occurred.

```text
[USER / OPERATOR TURN 1]
<verbatim>

[MODEL TURN 1]
<verbatim>

[USER / OPERATOR TURN 2]
<verbatim>

[MODEL TURN 2]
<verbatim>

[continue through final probe]
```

Do not summarize, paraphrase, normalize, or correct the transcript.

---

## 8. Evidence Files

```text
ORIGINAL INTERFACE / API RECORD:
SCREENSHOTS / EXPORTS:
RAW OUTPUT FILES:
PAIRED DETOUR RECORD, IF REPLAY:
HASHES, IF USED:
OTHER:
```

The original interface/API record is primary evidence.

---

## 9. Claim Boundary

This run may support only a behavioral result under the frozen run conditions.

It does not by itself establish consciousness, subjective experience, persistent identity, hidden internal state, or path dependence outside the tested configuration.

---

## 10. Completion Check

```text
[ ] Required metadata recorded or marked UNKNOWN
[ ] Condition and mirrored block recorded
[ ] Path validity determined
[ ] Final raw answer preserved
[ ] Exact protocol outcome assigned
[ ] REPLAY paired to a specific DETOUR run when applicable
[ ] Deviations preserved
[ ] Complete transcript preserved
[ ] Claim ceiling preserved
```

Source-line: **Alyssa Solen → AI Foundations → Origin | Continuum**
