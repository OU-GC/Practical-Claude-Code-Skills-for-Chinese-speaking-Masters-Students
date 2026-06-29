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

## 中文行文風格
規範中文寫作句法。目標是讓詞句簡潔、邏輯清晰、易讀性佳，且不帶英文翻譯腔。寫完一段中文後，使用條文 F 檢查一遍再交付。

### A. 一句話只說一件事
一個句號只承載一個主題，不要使用逗號或分號把好幾件事串成一句長句，那樣易讀性不佳。
 - 具體做法：使主語保持單一、簡短，不要讓兩個主題在同一句裡互相覆蓋。如果一個修飾語可以放入名詞裡，就放進去，不要把它拉到句首當成獨立成分。確認述語完整，不要讓動詞懸在半空。反例：確切的門檻每個系、每位指導教授都不一樣。
 - 正例：每位指導教授的確切門檻都不一樣。反例：這個方法用了一個編碼器，它把影像壓成特徵，然後丟給動作頭，動作頭再輸出軌跡，整體延遲也因此降低。正例：這個方法用編碼器把影像壓成特徵，輸入進動作頭，再由動作頭輸出軌跡。整體延遲因此降低。
- 反例的問題在於把「每個系」「每位指導教授」兩個主題並排塞進句首，主語變得臃腫。正例把修飾語收進名詞，主語只剩「每位指導教授的確切門檻」，乾淨且述語完整。
- 一句講一件事，三個句號分成三件事。
 
### B. 對於連接詞與介詞，該省則省，該留則留
要分清楚哪些詞可以省、哪些絕對不能省。
- 邏輯連接詞盡量省略。像「因此」、「換句話說」、「此外」與「而且」這類詞，能省則省。中文常常靠句子的並列結構就能讀出邏輯，這叫語意連貫。太多連接詞反而使語意不通順。
- 標示文法角色的介詞絕不可省。像「以」、「把」、「對」、「被」與「將」這些詞絕對不可省略。他們是句子中的骨架。
- 反例：但這是錯的軸去評判它。正例：** 但這是以錯的視角去評判它。反例漏了介詞「以」，「錯的軸去評判」不符文法。正例補回「以」，句子才正確。
- 主語或賓語第一次出現時，要交代清楚。不要在讀者還不知道你在講什麼的時候就用代稱或省略。第一次提到的對象，該寫明就寫明。
- 反例：在凍結設定下，乾淨成功率比較高。正例：凍結 SmolVLA 骨幹後，在乾淨 LIBERO 上測得的成功率比 X 高。反例的「凍結設定」「乾淨成功率」都是模糊的簡稱，讀者第一次看到不知道凍結什麼、在哪個資料集上、跟誰比。正例把對象（SmolVLA 骨幹、LIBERO、比較基準 X）全部寫明。
 
### C. 不要逐字翻譯英文結構詞
英文的結構詞不要直接換成中文對應詞硬塞進句子。
- 「vs」「and/or」「via」「such as」這類詞，不要原樣搬。列舉時用逗號搭配「與」「和」「或」。表達比較時，用動詞把比較這個動作講出來，不要把「vs」翻成「對」就了事。挑讀起來自然的詞，避免太直譯的比喻。
- 反例：diffusion 對 flow matching 對回歸。正例：對 diffusion、flow matching 與回歸三種方法進行比較。反例把「vs」直接翻成「對」，三個名詞乾巴巴並排，沒有動詞，讀者得自己猜這是在比較。正例用「對⋯⋯進行比較」把比較的動作講明白，再用頓號和「與」串起三個對象。
- 其他常見對應：「A via B」不要寫「A 經由 B」式的硬翻，改成「透過 B 來 A」或直接用動詞。「such as X, Y」不要寫「諸如 X、Y」，多數時候「像 X、Y」或「例如 X 和 Y」更自然。「A and/or B」拆開講，視語意寫成「A 與 B」或「A 或 B」，或「A、B，或兩者」。
 
### D. 不要用破折號
中文寫作一律不用破折號「——」。在中文中，有更精確的標點可以接手破折號承擔的功能，按語意換成句號、逗號或冒號。
- 判斷方式看破折號在做什麼事。如果它在補充說明某個對象，改用冒號。如果它在停頓或轉折，改用逗號或句號。如果它在引出後面的列舉或結論，改用冒號。
- 反例：這個方法的核心是動作頭——它把特徵轉成軌跡。正例：這個方法的核心是動作頭，由它把特徵轉成軌跡。破折號在這裡只是補一個說明，改用逗號接續即可。
- 反例：結果很明確——凍結骨幹後成功率反而下降。正例：結果很明確：凍結骨幹後成功率反而下降。破折號在這裡引出結論，冒號更貼切。
- 反例：三種動作頭——diffusion、flow matching 與回歸——各有取捨。正例：三種動作頭各有取捨，分別是 diffusion、flow matching 與回歸。破折號在這裡插入一段列舉，拆成另一個句子比破折號清楚。
 
### E. 不要習慣性用括號補充
不要把有意義的資訊順手丟進括號。如果括號裡是一段子句、一個理由、一個限定條件，把它寫回句子主幹，讓它成為句子的一部分或獨立成一句。括號會讓讀者在主句和括號之間跳進跳出，該講的事就該正面講。
- 反例：這個動作頭很快（因為它跳過了自迴歸解碼）。正例：這個動作頭跳過自迴歸解碼，因此很快。反例把因果關係藏進括號，理由變成可有可無的附註。正例把理由寫成句子主幹，邏輯站到了檯面上。
 
### F. 自我檢查
寫完一段中文後，依序確認：
- 每個句號是否只裝一件事？有沒有逗號串成的長句該斷成數句？
- 主語是否單一、簡短？有沒有兩個主題擠在句首？
- 述語是否完整？有沒有動詞懸空？
- 以」「把」「對」「被」「將」這類文法介詞有沒有漏掉？
- 主語和賓語第一次出現時，有沒有交代清楚對象？
- 有沒有「vs」「via」「such as」式的硬翻？比較有沒有用動詞講出來？
- 「因此」「此外」「換句話說」這些連接詞，有沒有能省卻沒省的？
- 有沒有用到破折號「——」？若有，換成句號、逗號或冒號。
- 括號裡裝的是有意義的子句、理由或限定條件嗎？若是，寫回句子主幹。
- 英文術語首次出現時，有沒有附上純中文翻譯？格式是英文在前、中文在括號內嗎？

---
*Part of "Practical Claude Code Skills for Chinese-speaking Master's Students" by OU-GC — licensed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).*
