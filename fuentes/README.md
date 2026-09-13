# Sources (`fuentes/`)

The PDFs behind the thesis citations, and the map that ties each BibTeX key to the file that was actually read. It exists so that verifying a citation (`../skills/reference-writting/source-fidelity.md`) never depends on a download that has to be repeated, or on memory of "which version we looked at".

This folder holds **literature**, not project facts (those live in `../project-context/`) and not thesis text (`../thesis/`).

## Layout

| Path | What it is |
| :--- | :--- |
| [`INDEX.md`](./INDEX.md) | One row per entry of `thesis/references.bib`: where it is cited, DOI or URL, local PDF, which version the PDF is (published, preprint, author version), how to obtain it, and whether its uses are verified. Plus the pending manual downloads and the SHA-256 of every local PDF. |
| `pdf/<bibtex-key>.pdf` | The file itself, named exactly like its BibTeX key (`pdf/gao-lowgpuutilization-2024.pdf`). **Local only**, see below. |

## Git policy: PDFs are not committed

**Confirmed by the authors on 2026-09-13.**

The repository is **public** on GitHub (checked 2026-09-13), and most papers are under publisher copyright or reachable only through the university's licences. Committing them would redistribute licensed content. So:

- `pdf/*` is ignored by `fuentes/.gitignore`. Only `INDEX.md` and this README are versioned.
- Each author keeps their own local copy. `INDEX.md` gives the exact DOI or URL and the SHA-256, so anyone can obtain the same file and confirm it is identical to the one that was verified.
- To share the PDFs among the authors, use a private channel (a shared university drive), not this repository.
- If the repository ever becomes private, the authors can decide to remove the ignore rule. That is their call, not an agent's.

## Where to look for a source

In this order. Stop at the first step that yields the full text.

1. **The published version in open access.** Many venues this thesis cites are open: USENIX (OSDI, NSDI, ATC), NeurIPS and MLSys proceedings, *IEEE Access*, SciTePress, npj journals.
2. **Portals licensed by Universidad Icesi** (Facultad de Ingeniería, Diseño y Ciencias Aplicadas):

   | Portal | Covers | Use for this PDG |
   | :--- | :--- | :--- |
   | **ACM Digital Library** | ACM journals, magazines, conference proceedings and books in computer science and IT | **Main portal.** ACM Computing Surveys, SOSP, EuroSys, ICSE, CCS… |
   | **Applied Science & Technology Source** (EBSCO) | Academic articles in computing, technology and engineering | Second option, especially for journals outside ACM |
   | **Knovel** | Engineering reference content and tools | Only for engineering handbooks or reference data |
   | ACS Publications | Chemistry, food technology, pharmacy, biochemistry | Out of this project's domain |
   | GreenFILE | Ecology, environment, sustainability | Out of domain |
   | DynaMedex · Micromedex · AccessMedicina | Clinical and pharmacological information | Out of domain |
   | WGSN | Trend analysis for marketing, design and fashion | Out of domain |

   IEEE Xplore, SpringerLink, ScienceDirect and Wiley are **not** on the list the authors provided. For papers there, look for the open-access or author version first, and otherwise ask the authors whether the university gives access by another route.
3. **An author or preprint version** (arXiv, the author's institutional page). Allowed for verifying paraphrases, but `INDEX.md` records it as a preprint. **A direct quotation or a page locator in the thesis must be checked against the published version**, because wording and pagination change.

Never use an abstract, a search-engine snippet, a blog post or an AI-generated summary in place of the full text.

## When an agent cannot download the file

Agents may search the portals' public pages (titles, abstracts, DOIs). Full-text downloads usually need the Icesi login or are refused to automated clients: ACM DL returned HTTP 403 to an agent on 2026-09-13. In that case the agent:

1. Does **not** write or keep the citation on the strength of the abstract.
2. Adds the key to *Pendientes de descarga manual* in `INDEX.md`, with the exact DOI or URL and what is missing (the whole paper, or only the published version).
3. Asks a person to download it with their university account and save it as `fuentes/pdf/<bibtex-key>.pdf`.
4. Once the file is there, computes its SHA-256, moves the row out of the pending table, and continues the verification.

## Keeping `INDEX.md` current

Update it in the same change that:

- adds or removes an entry in `thesis/references.bib`;
- adds, replaces or re-downloads a PDF (new SHA-256, and the *Versión del PDF* column if the version changed);
- verifies uses of a source in `thesis/CITAS-VERIFICADAS.md` (the *Verificada* column);
- changes where a key is cited (the *Citada en* column).
