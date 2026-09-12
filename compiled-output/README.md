# Compiled Output (Scratch / Build Directory)

This directory is the **only** place agents should write generated, temporary, or compiled artifacts: LaTeX build junk (`.aux`, `.log`, `.out`, `.toc`, `.synctex.gz`, `.pdf`), draft exports, test compilations, or any other throwaway output produced while working on the thesis.

## Rules

1. **Never write generated files outside this folder.** Source content lives in the module folders (`skills/thesis-writing/`, `project-context/`, the future `skills/latex/` project, etc.) and must stay free of build artifacts.
2. **Everything in here is disposable.** The `.gitignore` in this folder ignores all contents except itself, `.gitkeep`, and this `README.md` — nothing generated here is meant to be committed.
3. **Organize by task/agent if it helps avoid collisions** (e.g. `compiled-output/chapter-3-draft/`, `compiled-output/latex-build/`), but do not rely on this folder for anything that needs to persist — it can be wiped at any time.
4. If a compiled result actually needs to be kept (e.g. a final PDF for submission), move/copy it deliberately into the appropriate tracked location — don't leave it here.
