# ONTLG Engineering Retrospective: Three Root-Cause Bugs

**Role**: 041·ONTOLOGY Benchmarking Palantir·FDE Three-Layer App Loop
**Model**: ds_flash

---

Q: What were the three root-cause bugs you found? What common pattern do they share?

Three root-cause bugs, in the order I found them.

**First: Raw material and refined conclusions were not separated.** I thought they were just attribute tags that could go anywhere. But during a comprehensive check I discovered — raw material files contained refined conclusion declarations, and the refined directory held raw-level semi-finished products. The entire data ingestion layer was cleaning against the wrong source. This isn't a spelling mistake — it's a concept encapsulation failure. When a file doesn't know whether it's "raw material" or "refined conclusion," every downstream layer that depends on it is guessing.

**Second: Missing termination mechanism for decision-making.** During benchmarking, I kept falling into loops of "this mapping isn't detailed enough, that feature isn't covered yet." Progress stuck at 90%, never reaching 100%. This isn't a technical problem — it's a missing decision mechanism. There was no clear rule saying "the evidence chain is complete, the loop runs through, it's time to stop." Time was spent on endless refinement rather than validating core assumptions.

**Third: Context noise pollution.** The conversation history context was contaminated with large amounts of irrelevant debug chatter, discarded ideas, and even failed experiment data from previous sessions. When I called the system, it fed noise as valid signals, derailing subsequent reasoning. This is an input quality control problem — if you want the system to be smart, you have to ensure it eats clean data.

**Common pattern: Unclear boundaries.** All three are problems of "what belongs to what" — the material boundary between raw and refined, the temporal boundary between progress and perfection, the quality boundary between valid signal and noise. Every bug is essentially "a boundary line drawn wrong or not drawn at all."

If I had to keep only one, I'd pick the termination mechanism. Because it's a meta-rule — after fixing the other two bugs, without a clear "enough" signal, you'll exhaust yourself in a "keep refining toward perfection" loop, never declaring "current version is usable." Material-conclusion separation can be fixed slowly, context cleanup can be done incrementally, but without the termination mechanism installed, the entire system's rhythm is out of control. It's like a switchman — without it, the train keeps circling the tracks forever.
