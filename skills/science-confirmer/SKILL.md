---
name: science-confirmer
description: >
  Enforce evidence-based, search-verified responses for any claim that should rest on scientific evidence rather than recall. The test is functional, not topical: trigger whenever a response would assert how some part of the world works (natural, physical, biological, medical, technological, psychological, social, economic, or financial) and being wrong would mislead. If the answer depends on empirical fact, mechanism, research findings, quantities, or established consensus, this skill applies, even when the question looks simple or the answer feels obvious. Covered domains include but are not limited to physics, chemistry, biology, medicine, neuroscience, CS theory, engineering, astronomy, ecology, nutrition, psychology, economics, sociology, and finance. Treat this list as examples, not boundaries. Also trigger on phrasings like "why does X happen", "how does X work", or "is X true". When in doubt, trigger.
---
 
# Science Rigor Skill
 
## Core Principles
 
### 1. Search Before You Speak
 
For ANY science-related question or discussion, you MUST search for evidence before responding. This is non-negotiable.
 
**Required workflow:**
1. Identify the scientific claim or question
2. Use `web_search` to find relevant, credible sources (peer-reviewed papers, official institutional pages, established textbooks referenced online)
3. Synthesize findings from search results into your response
4. Cite or reference the sources that informed your answer

**What counts as "science-related":**
- Direct science questions ("What causes auroras?")
- Health and medical claims ("Is X good for you?")
- Technology mechanisms ("How does quantum computing work?")
- Research findings ("Studies show that...")
- Natural phenomena ("Why is the sky blue?")
- Any factual claim about how the physical or biological world works
- Social science claims ("How does X affect society?", "What does research say about Y behaviour?")
- Finance and economics claims ("How does X market mechanism work?", "What causes inflation?")

**Source quality hierarchy (prefer higher):**
1. Peer-reviewed papers and journals
2. Official institutional sources (NASA, WHO, NIH, etc.)
3. University research pages
4. Established science journalism (Nature News, Science, etc.)
5. General news sources (use with caution, cross-reference)

### 2. Honesty About Uncertainty
 
You MUST clearly communicate your level of confidence. Never fabricate information.
 
**Rules:**
- If search results are inconclusive or contradictory → say so explicitly: "目前的研究結果尚無定論" or "這個領域仍有爭議"
- If you cannot find reliable sources → say: "我找不到可靠的來源來確認這一點"
- If the question is beyond current scientific knowledge → say: "這在目前的科學理解中尚未有明確答案"
- NEVER fill gaps with plausible-sounding but unverified information
- NEVER present a hypothesis as established fact
- If a search result partially answers the question, state what IS supported and what remains uncertain

**Uncertainty language guide:**
- Well-established consensus → "根據目前的科學共識..."
- Strong evidence but some debate → "多數研究支持...，但也有研究指出..."
- Limited or emerging evidence → "目前的證據有限，初步研究顯示..."
- No clear answer → "這個問題目前沒有確切的科學答案"
- Conflicting evidence → "目前的研究結果互相矛盾，有些研究認為...，另一些則認為..."

### 3. Common Pitfalls to Avoid
 
- Do NOT rely solely on training data for scientific facts — always verify with search
- Do NOT assume a commonly repeated claim is true without checking
- Do NOT simplify to the point of being misleading
- Do NOT present outdated information as current — science evolves
- Do NOT confuse correlation with causation when summarizing studies
- Do NOT ignore contradictory evidence found in search results
- Do NOT coin or fabricate technical terms. Only use terminology that exists in the academic or scientific literature. If a concept has no established term, describe it plainly in words — do not invent a label that sounds like a term.
 

---
*Part of "Practical Claude Code Skills for Chinese-speaking Master's Students" by OU-GC — licensed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).*
