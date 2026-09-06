# APA Style 7th Edition Guidelines for Academic and Thesis Writing

A practical reference guide for formatting, citing, referencing, and presenting empirical tables and figures in academic theses, research papers, and dissertations according to the American Psychological Association (APA 7th edition) standard.

---

## 1. General Document Formatting

| Parameter                 | APA 7th Standard Specification                                                                                                                                                                                           |
| :------------------------ | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Page Margins**          | 1 inch (2.54 cm) on all sides (top, bottom, left, right). _(Note: If your institution requires binding, increase the left margin to 1.5 inches / 3.81 cm)._                                                              |
| **Typography & Fonts**    | Accessible, consistent fonts throughout the text:<br>• **Sans Serif**: 11-pt Calibri, 11-pt Arial, or 10-pt Lucida Sans Unicode.<br>• **Serif**: 12-pt Times New Roman, 11-pt Georgia, or 10-pt Computer Modern (LaTeX). |
| **Line Spacing**          | Double-space throughout the entire document, including block quotations, notes, and references.                                                                                                                          |
| **Paragraph Indentation** | Indent the first line of every paragraph by 0.5 inches (1.27 cm) using the Tab key. Do not add extra blank lines between paragraphs.                                                                                     |
| **Text Alignment**        | Align text to the left margin; leave the right margin ragged (do not full-justify unless required by local institutional guidelines).                                                                                    |
| **Page Numbering**        | Top right corner of the header on every page, starting with page 1.                                                                                                                                                      |

---

## 2. Heading Hierarchy (5 Levels)

APA uses five distinct heading levels to structure sections and subsections:

```text
Level 1: Centered, Bold, Title Case Heading
         Text begins as a new paragraph below.

Level 2: Flush Left, Bold, Title Case Heading
         Text begins as a new paragraph below.

Level 3: Flush Left, Bold Italic, Title Case Heading
         Text begins as a new paragraph below.

Level 4: Indented 0.5 in., Bold, Title Case Heading, Ending With a Period. Text begins on the same line.

Level 5: Indented 0.5 in., Bold Italic, Title Case Heading, Ending With a Period. Text begins on the same line.
```

---

## 3. In-Text Citations

In-text citations indicate the intellectual source of claims, data, models, or quotations. APA 7 uses the author-date citation system.

### A. Author Count Rules

| Author Count                               | Parenthetical Citation                                                                 | Narrative Citation                                                     |
| :----------------------------------------- | :------------------------------------------------------------------------------------- | :--------------------------------------------------------------------- |
| **1 Author**                               | `(Smith, 2021)`                                                                        | Smith (2021) stated that...                                            |
| **2 Authors**                              | `(Smith & Jones, 2020)` _(use ampersand &)_                                            | Smith and Jones (2020) demonstrated... _(spell out "and")_             |
| **3 or More Authors**                      | `(Smith et al., 2022)` _(from the very first citation)_                                | Smith et al. (2022) revealed that...                                   |
| **Group / Organization with Abbreviation** | First citation: `(World Health Organization [WHO], 2021)`<br>Subsequent: `(WHO, 2021)` | First: World Health Organization (WHO, 2021)<br>Subsequent: WHO (2021) |
| **Group without Abbreviation**             | `(Stanford University, 2023)`                                                          | Stanford University (2023) reported...                                 |

### B. Direct Quotations vs. Paraphrasing

- **Paraphrasing (Preferred in Empirical Theses):**
  > _"Distributed microservices reduce single-point failure risks but increase network serialization overhead (Hernandez & Gomez, 2022)."_
- **Short Direct Quotation (<40 words):** Enclose in double quotation marks and provide the specific page or paragraph number.
  > _"According to Dijkstra (1972), 'program testing can be used to show the presence of bugs, but never to show their absence' (p. 6)."_
- **Block Quotation (≥40 words):**
  - Indent the entire block 0.5 inches (1.27 cm) from the left margin.
  - Do not use quotation marks.
  - Double-space the block.
  - Place the citation **after** the closing punctuation mark of the quotation:
    > In empirical software engineering, architecture decisions must consider long-term maintainability:
    >
    > > Technical debt is not simply bad code; it is the deliberate or inadvertent deferral of architectural evolution to satisfy immediate delivery milestones. When left unmanaged, the cumulative compounding of interest degrades throughput until teams allocate the majority of sprints to regression containment. (Kruchten et al., 2019, p. 112)

---

## 4. Tables and Figures Formatting

Both tables and figures follow identical structural components in APA 7th:

1. **Number** (`Table 1` or `Figure 1`): Bold, flush left, above the title.
2. **Title**: Italic, title case, flush left, double-spaced below the number.
3. **Body / Canvas**: Clean display without vertical lines in tables.
4. **Note**: Flush left below the table or figure, beginning with italicized _Note._ Explains abbreviations, data sources, or statistical significance symbols ($*p < .05$).

### Example Table Layout:

```text
Table 1
Baseline Performance Metrics Across Evaluated Architectures

─────────────────────────────────────────────────────────────
Architecture       Latency (ms)     Throughput (req/s)    CPU (%)
─────────────────────────────────────────────────────────────
Monolithic             42.5               1,240            68.2
Microservices          88.1               3,450            82.4
Serverless            115.0               2,890            54.1
─────────────────────────────────────────────────────────────
Note. Values represent the arithmetic mean across 10 benchmark
trials under simulated load. CPU utilization is normalized to 8 cores.
*p < .05. **p < .01.
```

---

## 5. Reference List Architecture

- Start on a new page after the text, titled **References** (bold, centered).
- Alphabetize entries by the first author's surname.
- Use a **hanging indent** of 0.5 inches (1.27 cm) for each entry.
- Provide DOI URLs formatted as `https://doi.org/...` whenever available.

### Standard Reference Formats:

#### 1. Journal Article with DOI:

> Author, A. A., & Author, B. B. (Year). Title of the journal article in sentence case. _Title of Periodical in Italics and Title Case_, _VolumeNumber_(IssueNumber), PageRange. https://doi.org/xxxxxxx
>
> _Example:_  
> Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, Ł., & Polosukhin, I. (2017). Attention is all you need. _Advances in Neural Information Processing Systems_, _30_, 5998–6008. https://doi.org/10.48550/arXiv.1706.03762

#### 2. Authored Book:

> Author, A. A. (Year). _Title of the book in italics and sentence case_ (Edition, if any). Publisher Name.
>
> _Example:_  
> Fowler, M. (2018). _Refactoring: Improving the design of existing code_ (2nd ed.). Addison-Wesley Professional.

#### 3. Edited Book Chapter:

> Author, A. A. (Year). Title of chapter. In E. E. Editor (Ed.), _Title of book in italics_ (pp. xx–xx). Publisher Name.

#### 4. Conference Proceedings Paper:

> Author, A. A., & Author, B. B. (Year). Title of paper. In C. C. Chair (Ed.), _Proceedings of the Title of Conference_ (pp. xx–xx). Publisher. https://doi.org/xxxxxxx

#### 5. Technical Report / Institutional White Paper:

> Organization Name or Author. (Year). _Title of report in italics_ (Report No. xxx). Publisher or Organization. URL

---

## 6. Common APA Pitfalls to Avoid

- ❌ **Using "et al." incorrectly in citations:** In APA 7, 3+ authors use `et al.` on the very first citation. Do not write out all authors first.
- ❌ **Ampersand (&) misuse:** Use `&` inside parenthetical citations `(Smith & Jones, 2020)` and tables; use the word `and` in narrative prose `Smith and Jones (2020) demonstrated...`.
- ❌ **Vertical lines in tables:** APA strictly forbids vertical grid lines in empirical tables. Use only horizontal rules (top, header-bottom, table-bottom).
- ❌ **Missing DOIs or broken URLs:** Always include active DOIs formatted as `https://doi.org/...` rather than `doi:10.xxx`.
- ❌ **Over-quoting:** Empirical scientific theses value critical synthesis and paraphrasing over direct quotations. Restrict quotes to definitions or seminal statements.
