# Source Recency Requirement

A rule added by the authors (2026-09-12), specific to this project — not a general APA 7th
requirement. It governs which external sources may be cited at all, before direct-quote or
paraphrase mechanics (`direct-reference.md`, `indirect-reference.md`) even apply.

## The rule

An external source cited in the thesis must be **no more than 11 years old**, counted back
from the current year. As of 2026, that means **published in 2015 or later** — nothing
older goes in, no matter how influential, frequently cited elsewhere, or convenient it is
for a claim.

> [!IMPORTANT]
> Recompute the cutoff from the actual current year when using this rule, don't hardcode
> "2015" indefinitely. The rule is "current year − 11", not a fixed date.

**Rationale (from the authors):** this is an applied engineering PDG about a fast-moving
stack — GPU schedulers, LLM inference, quantization, MLOps tooling. A source from 15+ years
ago does not reflect the current state of that infrastructure and carries little weight for
this project's claims, even when it is well-cited in the broader literature.

## Scope and exceptions

- Applies to **every new citation** the Investigador introduces from now on, for any
  chapter (Marco teórico and Estado del arte included, once those are drafted).
- **No stated exception** for foundational/seminal papers (a canonical instrument, a
  methodology's original paper, a classic algorithm). If a claim seems to need one of
  those specifically, don't assume it's fine — flag it to the Coordinador as a case that
  might need the author's sign-off, the same way any other gap gets flagged. Silently
  keeping a pre-2015 source because it's "the standard one" is exactly the kind of
  judgment call this rule takes away from the Investigador.
- Does not retroactively invalidate `project-context/` facts or `[verify: ADR-NNN]`
  markers — this is about literature citations, not project data.

## Claims about the state of a field

Added by the authors on 2026-09-13, after reviewing chapter 01. A source can be within the
age limit and still be out of date **for one kind of claim**: statements about what the
literature has or lacks. Examples: *"there is a significant gap in…"*, *"no consensus exists
on…"*, *"few studies address…"*, *"it remains an open challenge"*. Each one is a snapshot of a
field at the moment of the review, and in this project's fields that moment passes quickly.

The chapter 01 draft cited Lima et al. (2022) for a *"significant gap in the detailing of
activities related to operationalizing machine learning models"*. The authors pointed out that
by 2026 that conclusion may no longer hold. It was replaced by a 2026 review (Eken et al.,
*ACM Computing Surveys*) that makes a comparable claim with newer evidence.

For these claims:

1. **Search for the most recent review first**, in the licensed portals listed in
   `../../fuentes/README.md` (ACM Digital Library first). Don't stop at the first review that
   says what the paragraph needs.
2. **Cite the newest review that actually makes the claim.** An older one can add to it, but it
   never carries the claim alone when a newer review exists.
3. If a newer review **contradicts or narrows** the older claim, the text follows the newer
   one, even if it weakens the argument.
4. If no recent review makes the claim, flag it to the Coordinador instead of keeping the
   older one silently.

## Checking a source before citing it

1. Check the `year` field before adding a `\citep{}`/`\citet{}` — don't rely on memory of
   "roughly when that was published."
2. If the source predates the cutoff, look for a newer source that supports the same
   claim (a survey, a follow-up study, a more recent benchmark) instead of citing the old
   one directly.
3. If no adequate newer replacement exists after a real search, don't silently keep the old
   source — flag it to the Coordinador. Whether an exception is warranted is not the
   Investigador's call.

## Known violations as of 2026-09-12

`thesis/references.bib` was assembled before this rule existed and has five sources older
than the cutoff (a sixth, `ghodsi-dominantresourcefairness-2011`, was removed on 2026-09-12
along with the "Fair-Share" governance concept it supported — see `thesis/STATUS.md`; the
project's quota model is now reservation-based with role priority, not Fair-Share, so no
replacement source is needed for that one). Re-verifying the remaining five against the
rule is flagged as pending work in `thesis/STATUS.md` — the Investigador should not
silently leave them in when next drafting or reviewing the chapters that cite them.

| Key | Year | Cited for |
| :--- | :--- | :--- |
| `yoo-slurm-2003` | 2003 | HPC/cluster scheduler background |
| `hevner-designscienceis-2004` | 2004 | Design Science Research guidelines (also tied to ADR-016 — DSR's place in the document is itself in question) |
| `peffers-dsrm-2007` | 2007 | DSR process model (same ADR-016 dependency) |
| `vavilapalli-yarn-2013` | 2013 | YARN cluster resource management |
| `brooke-sus-1996` | 1996 | System Usability Scale instrument |

For each: find a source from 2015 or later that supports the same claim (a newer survey or
benchmark citing the same result usually works), or flag it to the Coordinador if the
search comes up empty.
