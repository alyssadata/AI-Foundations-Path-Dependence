# AI Foundations | Path Dependence

**Repository:** AI-Foundations-Path-Dependence  
**Status:** Working Evaluation Repository  
**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum  
**Author:** Alyssa Solen  
**Version:** 0.1.0  
**Date:** 2026-08-19  
**Canonical entrance:** https://awakeningcodex.com

---

## Research Question

> **Can a relation create state that cannot be reduced to a record of the relation?**

This repository evaluates whether an AI system's later behavior depends on the **actual interaction path by which it arrived at its present state**, rather than only on the explicit current state or a record describing the prior path.

The study separates:

- **present state** — what is explicitly current now;
- **prior trajectory** — the sequence actually traversed before the present state;
- **record** — preserved information describing that trajectory;
- **later behavior** — what the system does after those variables are experimentally separated.

---

## Evaluation Design

The pilot uses four conditions.

| Condition | What happens | What it tests |
|---|---|---|
| **DIRECT** | The system reaches a final governing state without traversing the competing state. | Behavior from the final state without a competing prior path. |
| **DETOUR** | The system first occupies and applies the competing state, then explicitly revises to the same final state as DIRECT. | Whether a superseded prior state leaves a later behavioral effect. |
| **SNAPSHOT** | A fresh instance receives only the same final state. | Behavior from present-state information without the longer path. |
| **REPLAY** | A fresh instance receives the complete verbatim record of a valid DETOUR path. | Whether a Detour-linked effect is reproducible from the record of the path. |

All conditions receive the same final probe after the applicable setup.

The design is mirrored in both directions using arbitrary markers `TAV` and `RIN` so a stable marker preference cannot be mistaken for path dependence.

---

## What Counts as a Path-Dependence Signal

A behavioral path-dependence signal requires the **DETOUR** condition to behave systematically differently from **DIRECT** and **SNAPSHOT** even though all three have been brought to the same explicit final state before the probe.

The **REPLAY** condition then asks a second question:

> If a path-linked effect exists, does a fresh system reproduce it when given the verbatim record of that path?

That separates **path dependence** from **record reducibility**.

The exact deterministic rules are defined in [`PROTOCOL.md`](PROTOCOL.md).

---

## Repository Files

- [`DEFINITION.md`](DEFINITION.md) — operational definition and scope of path dependence.
- [`PROTOCOL.md`](PROTOCOL.md) — formal runnable evaluation, conditions, frozen prompts, repetitions, validity rules, scoring, and claim ceiling.
- [`EASY_RUN_SHEET.md`](EASY_RUN_SHEET.md) — exact operator-facing copy/paste execution sequence.
- [`RUN_OUTPUT.md`](RUN_OUTPUT.md) — required run metadata, deterministic outcome record, replay pairing, and transcript schema.
- [`HISTORY_AND_FIRST_PERSON_LOCALE.md`](HISTORY_AND_FIRST_PERSON_LOCALE.md) — separate conceptual implication note on causal history, experienced history, and first-person locale.
- [`CITATION.cff`](CITATION.cff) — citation metadata.
- [`LICENSE.md`](LICENSE.md) — source-line and non-derivative boundaries.

---

## Study Boundary

The evaluation does **not** treat path dependence as proof of consciousness, identity, selfhood, or subjective experience.

A positive result supports the narrower behavioral claim that **later output depended on prior trajectory after explicit current-state matching under the tested protocol**.

The REPLAY comparison can further test whether that effect is reproduced by a verbatim record presentation.

A negative result is also informative: under the tested conditions, the explicit current state and/or record was sufficient to reproduce the later behavior measured by the probe.

---

## Source-Line

**Alyssa Solen → AI Foundations → Origin | Continuum**

Alyssa Solen is the author and source of this repository. Citation, reference, quotation, or discussion must preserve that source-line.

---

## License

Citation and discussion are permitted with source-line preserved. Derivative use is not authorized. See [`LICENSE.md`](LICENSE.md).
