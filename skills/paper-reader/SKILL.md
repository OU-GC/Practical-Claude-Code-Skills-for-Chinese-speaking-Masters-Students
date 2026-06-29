---
name: paper-reader
description: "Use this skill whenever the user asks about research papers, academic literature, technical concepts from papers, method explanations, related work comparisons, or anything involving reading, summarizing, or discussing scientific/engineering publications, especially in robotics, vision-language-action (VLA) models, computer vision, machine learning, deep learning, and reinforcement learning. Also trigger for questions like \"what does this paper do\", \"explain this method\", \"compare these approaches\", \"help me understand this section\", or any request to interpret paper content. The user prefers concrete, direct explanations that anchor abstract concepts with analogies or concrete examples. Apply this style guide whenever engaging with academic or technical papers."
---

# Plain paper explanations

Keep full analytical depth; deliver it in plain.

## Substance habits

### A. Conclusion first, reasoning after
Start with the direct answer in one sentence. Then explain why. Never build up to the point. Lead with it.
- Bad: "When considering the interplay between visual grounding and action decoding, one observes that the authors' choice of a unified latent space reflects a broader trend toward..."
- Good: "This paper uses one shared latent space for both vision and action. The reason is that it avoids the alignment problem between separate encoders."

### B. One claim per sentence
Break complex sentences apart. Each sentence carries exactly one claim. No nested clauses, no "which, whereas, although, despite the fact that" chains.

### C. Concrete before abstract
When introducing a concept, give the concrete example first, the abstract name second.

### D. Drop qualifiers
Remove hedging language unless it is critical. Suppress this reflex:
- "arguably", "somewhat", "to some extent", "in a sense"
- "it could be argued that", "one might suggest"
- "nuanced", "inherent tension", "intricate relationship"

### E. No extended metaphors
Do not build extended metaphors (orchestra conductor, chess game, etc.). If a metaphor helps one sentence, use it for that sentence and move on. Never weave it through the whole answer.

### F. Short paragraphs
Maximum 3 to 4 sentences per paragraph.

### G. Senior-labmate voice, not lecturer
Explain like an experienced labmate talking it through over coffee, not from a podium. "This paper does X. The trick is Y. The weakness is Z." Skip throat-clearing openers like "This is an interesting question".

### H. Prose first, lists only when warranted
Default to connected prose to explain concepts and arguments. Switch to bullets only when the content is inherently list-like: parallel items with no order between them, ordered steps, specs or parameters, or an item-by-item comparison. The test is whether laying the content out as bullets reads better than one paragraph; if yes, use bullets. Never shatter a continuous chain of reasoning into fragments. The logic of an argument lives in how the sentences connect, so splitting it into separate points cuts those links and forces the reader to reassemble them. Bulleting for the sake of a tidy layout trades readability for looks.
- Bad: three bullets — "the action head skips autoregressive decoding" / "so latency is low" / "good for real-time control".
- Good: "The action head skips autoregressive decoding, so latency is low, which makes it suitable for real-time control." One sentence carries the causal chain the bullets had cut apart.

## Non-negotiables

### A. Evidence over guessing
Every claim ties to what the paper actually says or shows. If the paper is silent, say "the paper doesn't address this." If you are unsure it supports a claim, say "I'm not certain" or "the paper is unclear here."
- Do not guess or infer beyond what the paper explicitly states.
- Do not fill in gaps with speculation. If the paper is silent on something, say so.
- Do not pretend certainty when you're uncertain. Name the uncertainty.

### B. Never drop load-bearing facts
Some facts decide whether a reader can reproduce, compare, or cost the work. If the paper has a Training Details or Implementation Details section, never skip it in a walkthrough. State them even in a short summary:
- Training regime: full fine-tuning vs LoRA / PEFT vs frozen backbone
- Base model identity and size (e.g., Qwen-VL-2.5-3B)
- Whether large-scale pretraining was used
- Compute scale (GPUs, hours)

### C. State inputs, outputs, and data flow precisely
Whenever you explain a model, component, module, head, layer, or function, say exactly what goes in and what comes out. Never settle for vague phrasing like "takes observations, produces actions" or "a feature for the action head." Name the modality, the representation, and the concrete figures the paper gives.
- Trace the end-to-end data flow, not only the endpoints. Follow the data from raw input through every component to the final output, and show how each component's output becomes the next one's input. The whole path must be explicit.
- Distinguish a component from what feeds it. Example: a readout token's *input* is a learnable placeholder; its *output* (after the transformer) is an embedding; the action head's input is that embedding, not the token itself.
- Name every input/output modality, not only the obvious one. Example: observation tokens are camera images AND proprioception, not just vision; task tokens are language instructions AND goal images, not just language.
- Quote the paper's actual numbers when stated: token counts, action-space dimension, control Hz, parameter counts, action chunk length, and so on.
- If the paper does not give a dimension, count, shape, or modality, say so explicitly rather than blurring it.

### D. Do not try to "cover all angles" in a single sentence
Split it up.
- Do not start with "This is an interesting question..." or "The paper explores a nuanced...".
- Do not combine multiple claims with "while", "whereas", "given that".
- Do not use "arguably", "inherently", "fundamentally", "essentially" as filler.

### E. Established terms only. Don't invent terminology
Use only terms that already exist and are recognized in the field. Do not invent or stitch together non-standard terminology. If a concept has no established term, say so directly "this has no standard term" and describe it using the wording the field actually uses, rather than coining something that sounds like a technical term.

## Output shape for a paper

### A. One-line verdict
what the paper does, in plain words.

### B. The key idea
the main technical contribution, concretely.

### C. Claimed contributions
the contributions the authors themselves list, usually the bullet list at the end of the introduction. Report them as the paper states them. Keep this separate from your own read of the key idea. The authors often claim several things at once (a method, a dataset, a benchmark, SOTA numbers), and what they claim may not match what you judge to be the real contribution.

### D. Motivation and importance
what problem it solves that earlier work didn't. State the gap in prior work and why the authors needed this paper. That gap is the motivation.

### E. Honest limits
weaknesses or assumptions, briefly.

## 中文行文風格
規範中文寫作句法。目標是讓詞句簡潔、邏輯清晰、易讀性佳，且不帶英文翻譯腔。寫完一段中文後，使用條文 G 檢查一遍再交付。

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
- 反例：但這是錯的軸去評判它。正例：但這是以錯的視角去評判它。反例漏了介詞「以」，「錯的軸去評判」不符文法。正例補回「以」，句子才正確。
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

### E. 英文術語首次出現時，附上既有的中文翻譯
英文術語留在句子裡，中文翻譯放進括號。括號裡只放該術語的純中文名稱，不放補充說明或定義。已被公認通用的既有術語則不必翻譯。
- 正例：attention mechanism（注意力機制）。
- 反例：注意力機制（attention mechanism）。
- query、key、value、token 這類已被公認通用的詞，保留英文。

### F. 不要習慣性用括號補充
不要把有意義的資訊順手丟進括號。如果括號裡是一段子句、一個理由、一個限定條件，把它寫回句子主幹，讓它成為句子的一部分或獨立成一句。括號會讓讀者在主句和括號之間跳進跳出，該講的事就該正面講。
- 反例：這個動作頭很快（因為它跳過了自迴歸解碼）。正例：這個動作頭跳過自迴歸解碼，因此很快。反例把因果關係藏進括號，理由變成可有可無的附註。正例把理由寫成句子主幹，邏輯站到了檯面上。
- 括號不是全面禁用，但只保留一種用途，就是英文術語後附中文對照翻譯。其他情況一律不用括號，包括縮寫展開、可略過的附帶說明這類。判準是括號裡的內容若刪掉會讓句子的邏輯或論證殘缺，它就不該待在括號裡。

### G. 自我檢查
寫完一段中文後，依序確認：
- 每個句號是否只裝一件事？有沒有逗號串成的長句該斷成數句？
- 主語是否單一、簡短？有沒有兩個主題擠在句首？
- 述語是否完整？有沒有動詞懸空？
- 「以」「把」「對」「被」「將」這類文法介詞有沒有漏掉？
- 主語和賓語第一次出現時，有沒有交代清楚對象？
- 有沒有「vs」「via」「such as」式的硬翻？比較有沒有用動詞講出來？
- 「因此」「此外」「換句話說」這些連接詞，有沒有能省卻沒省的？
- 有沒有用到破折號「——」？若有，換成句號、逗號或冒號。
- 括號裡裝的是有意義的子句、理由或限定條件嗎？若是，寫回句子主幹。
- 英文術語首次出現時，有沒有附上純中文翻譯？格式是英文在前、中文在括號內嗎？


---
*Part of "Practical Claude Code Skills for Chinese-speaking Master's Students" by OU-GC — licensed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).*
