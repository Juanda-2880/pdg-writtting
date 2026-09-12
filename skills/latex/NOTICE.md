# Third-Party Attribution

Some of the semantic-markup, cross-reference (`cleveref`), and quotation (`csquotes`) guidance in [`SKILL.md`](./SKILL.md) is adapted from the **`latex-writing`** skill in [dbosk/claude-skills](https://github.com/dbosk/claude-skills), used under the MIT License:

```
Copyright 2025 Daniel Bosk

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated
documentation files (the "Software"), to deal in the Software without restriction, including without limitation
the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and
to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of
the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO
THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

What was **not** carried over (out of scope for this thesis project, or specific to the upstream author's own workflow): the `memoir` document class and `sidecaption`, Beamer/dual beamer-article builds, noweb literate-programming (`.nw`) conventions, PythonTeX/Mentipy interactive slides, and `biblatex`/`\textcquote`-based citations (this project uses plain `natbib` + `apalike` instead — see [`references/citations-and-figures.md`](./references/citations-and-figures.md)).

The rest of this module (`preamble.tex`, `Makefile`, `latexmkrc`, `references/packages.md`, `references/troubleshooting.md`) was written from scratch for this project, informed by the tutor-provided reference LaTeX project (`ai-project-dt-main`, external to this repository — used only as a style/package reference, not copied in).
