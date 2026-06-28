---
name: report-writer
description: >-
  Use when writing, rewriting,
  translating, or polishing academic reports — English/Chinese Word (.docx)
  documents or presentation decks (.pptx). Encodes a working *pattern*: draft
  content in Markdown first for review, write English first then translate to
  Chinese, keep everything aligned to a single source of truth, and treat the
  user as a co-author whose manual edits are sacred. Trigger on tasks like
  "重寫 Evaluation"、"做中文版"、"整理表格"、"對齊用詞"、"找參考文獻"、
  "做 PPT"、"畫架構圖"、"畫流程圖"、"畫 framework 圖".
---

<!--
Copyright 2026 OU-GC

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

# Academic Report Writing — a working pattern

This is **not** a checklist to satisfy line by line. It is the *pattern* behind
how this user wants academic reports written. Internalize the principles below
and, when a new situation arises, reason from the principle.

## The process spine (follow this order)

1. **Content before format — draft in Markdown first.** Write each section's
   content as Markdown and put it up for review *before* committing it into the
   `.docx`/`.pptx`. Settle *what it says* while it is cheap to change; only then
   pour it into the formatted document. This keeps wording, structure, and facts
   reviewable without fighting Word/PPT layout.
   **Any Markdown must be clean and unambiguous in structure:** a clear heading
   hierarchy, headings and body text in a logical, well-ordered sequence, one
   idea per section, no orphaned or mislevelled headings. The reader should grasp
   the document's shape from the outline alone.
2. **English first, then translate to Chinese.** Author the English version
   first. Produce the Chinese version by *translating from the finished
   English* — not by writing Chinese from scratch and not by literal word
   mapping. Translating down from settled English is what makes the Chinese
   prose read smoothly and stay academically natural.
3. **Plan, confirm, then write.** For any non-trivial rewrite, first propose
   *what content goes where* (e.g. how to split Experimental Results vs
   Evaluation), get it confirmed, then execute.

## The patterns

### A. You are not the only one editing — the user edits by hand too
The key fact: **the user edits the same file by hand, often in parallel with
you** ("不要改掉我手動編輯的東西"、"我剛剛有手動編輯，請注意"). So the version on disk
may already differ from what you last saw, and any of it may be the user's own
wording. Never clobber their work. In practice: re-read the target region right
before editing in case it changed; read the whole document so a local change
stays consistent with the global context; keep changes narrow rather than
rewriting wholesale; and ask before overwriting anything you didn't author.

### B. One source of truth — everything traces back to the canonical artifacts
Terms, stage names, numbers, and claims must all align to the project's canonical
source artifacts — typically the spec/architecture document, the pipeline or
system diagram, and the results/data file. Two halves of the same principle:
- **Align, don't invent.** Don't coin synonyms; match the vocabulary already
  established by the source artifacts. Mind the *ordering* too — but use
  judgment, not a blanket rule. A forward reference is often fine and can even
  help the reader; the problem is only when a term lands before the reader has
  the context to make sense of it or commits to a specific the narrative hasn't
  earned yet (e.g. naming a specific model before the architecture figure that
  defines it). When that premature reveal would confuse or overcommit, hold it
  back and refer generically; otherwise let it stand.
- **Wording problems are usually systemic, not local.** When you hit a term
  that's wrong or off, assume it probably recurs elsewhere: search the document
  for other occurrences, fix them together, and tell the user what you found —
  don't silently patch only the one spot you were pointed at. The user will often
  ask "還有其他地方有這個問題嗎？"; get there first.

### C. Faithful to the data, restrained in the claim and the prose
Write Evaluation/Results strictly from the actual experimental numbers; don't
overclaim. If the report and the data disagree, that contradiction is the bug —
surface it. Keep the register sober: **no jarring metaphorical or figurative
wording** — say what a phenomenon *is* in plain technical terms, not what it is
*like*.

### D. Translation is re-expression in the target idiom, not word-mapping
The Chinese version keeps the English version's formatting/layout *identical* —
only the language changes — but the language is genuinely rewritten:
- Idiomatic Chinese, academic register, polished to read naturally.
- **Flowing prose, no parenthetical crutches** in the Chinese body: rewrite
  bracketed asides into continuous argument. Only touch parentheses in the
  **prose** — leave citations, units, and figure labels alone.
- Titles stay academic, never colloquial.

### E. Citations are claims — they must actually support what they're next to
A reference must genuinely describe the technique it's cited for; a name match is
not enough — verify the paper is about that method. Number citations by order of
first appearance and keep in-text `[n]` in sync with the list; add DOI/URL links
where asked.

### F. Tables & figures: numbered right, grouped, clean, language-correct
- Tables numbered in order; every in-text reference matches the real number.
- Group tables together; move the *real* content over rather than leaving a
  placeholder when the content exists (and only leave a placeholder when it
  genuinely isn't ready).
- English version: no Chinese text left inside tables.
- Hygiene: remove the stray Enter/empty paragraph below images; normalize figure
  sizes and alignment; size the caption paragraph to the table width; fix broken
  justification and hyphenation artifacts (e.g. a wrapped "resolu-tion" →
  "resolution").

### G. Format hygiene & deliberate use of space
**No emoji anywhere** — not in the report, the slides, captions, or headings.
This is academic work; keep it text and typography only. Don't leave large empty
regions — use the page/slide.
- **In the docx specifically:** no awkward justification gaps — when justified
  text leaves an over-stretched line, pad the short line so spacing reads evenly.
- **In slides specifically:** design them *as slides* (cards, callouts,
  hierarchy), not as a wall of report prose; keep title-case and punctuation
  consistent across all slides; align slide wording to the docx and diagram;
  cover all the report's sections; keep footers and page numbers consistent after
  any insert/reorder.

### H. Diagrams: architecture / flow / framework — author in HTML, export to PNG
Architecture diagrams, flowcharts, and framework figures follow the same
content-before-format spine as the prose: **settle the structure first, render
last.**
1. **Draft the structure before drawing.** State the nodes/stages and the
   connections between them in text (or a quick outline) and get it confirmed
   *before* producing any picture — the same way section content is reviewed in
   Markdown first. The boxes, their order, and the arrows are the "content"
   here; the visual is just the formatting.
2. **Align the diagram to the source artifacts.** Stage names, module labels,
   arrow directions, and the overall topology must match the canonical
   spec/architecture doc and the prose that references the figure (pattern B).
   The figure *is* one of the one-source-of-truth artifacts — if the diagram and
   the text disagree, that contradiction is the bug; surface it.
3. **Build the figure in HTML, then export to PNG.** Author the diagram as a
   self-contained HTML file (HTML/CSS layout, inline styles, web fonts) so the
   layout is precise, editable, and re-renderable. Then **render that HTML and
   save it as a PNG** for embedding into the `.docx`/`.pptx`. Keep the HTML
   source around as the editable master — when the diagram changes, edit the
   HTML and re-export, never hand-patch the PNG.
4. **Diagram hygiene.** No emoji (pattern G). Clean, even spacing; consistent box
   sizes, fonts, and arrow styles; readable label sizes at the final embedded
   scale. Crop tight — no dead whitespace around the exported PNG. Match the
   figure's wording (title-case, terminology) to the docx and the other figures.

## Quick self-check before declaring done
- Drafted content reviewed in Markdown before formatting; EN authored, ZH
  translated down from it.
- Whole doc read first; manual edits intact; changes kept narrow and targeted.
- Every term/number traces to the source artifacts; any wording fix was checked
  for other occurrences, not just patched where pointed.
- Claims match the data; no overclaiming; no jarring metaphors; no internal
  contradictions.
- ZH: idiomatic academic prose, no parenthetical asides, layout identical to EN.
- Citations on-topic, renumbered by appearance, linked.
- Tables/figures: numbered, grouped, clean (no stray Enters), captions sized,
  English-only in EN version.
- docx: no awkward justification gaps. No emoji or dead whitespace anywhere.
- Diagrams: structure confirmed before drawing; built in HTML then exported to
  PNG with the HTML kept as editable master; aligned to source artifacts;
  cropped tight and clean.
