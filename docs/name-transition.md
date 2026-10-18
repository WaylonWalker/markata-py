# Python Markata -> markata-py: identity transition

This repository is the original **Python** static site generator. The Go implementation is becoming **Markata** for its 1.0 release line; this Python implementation remains available historically as **markata-py**.

## What will change

- GitHub repository: `WaylonWalker/markata` (Python) -> `WaylonWalker/markata-py`.
- The Go repository `WaylonWalker/markata-go` will then become `WaylonWalker/markata`.
- Python package imports (`import markata`), current Python configuration (`markata.toml`), and historical tags/releases remain untouched during the repository transition.
- PyPI currently uses the `markata` project name for Python. **There is no automatic PyPI rename or transfer in a GitHub rename.** Existing Python users should pin their last compatible Python version, e.g. `markata<1`, if the 1.x name is later transferred to the Go distribution. The eventual `markata-py` PyPI packaging and CLI name require their own release work; do not assume `pip install markata-py` exists yet.

## Important GitHub link collision

Do **not** rely on a redirect from `WaylonWalker/markata` after the Go project claims that path. GitHub redirects old repository links only while their old path is unoccupied. Because the Go repository will reuse `WaylonWalker/markata`, the old Python URL will eventually lead to Go instead.

Update Python repository links and downstream Git remotes explicitly to `https://github.com/WaylonWalker/markata-py`.

```bash
git remote set-url origin https://github.com/WaylonWalker/markata-py.git
```

Avoid installing the Python and Go executables under the same `markata` path. Keep Python pinned/in its own virtual environment. Existing Python sites must not silently start using the Go CLI simply because the executable name matches.

## Owner cutover checklist

1. Confirm GitHub releases, tags, branch protections, Actions secrets, Pages configuration, PyPI publishing and any existing Python consumers before renaming.
2. Rename **this** Python repository to `markata-py` using GitHub repository settings; preserve all Git history and existing releases.
3. Update package metadata, homepage/source/issue URLs and documentation references in a separate follow-up commit. Keep the existing Python import name until a deliberately versioned Python package migration.
4. Once `WaylonWalker/markata` is free, rename the Go repository `markata-go` -> `markata`.
5. Verify both repository URLs, existing checkouts, release downloads, Go import paths, CI and container builds. Do not assume old Python GitHub links are redirected to Python.
6. Publish an audited Go `1.0.0-rc.1` before deciding whether and how the PyPI project name can be reused. No automated 1.x Python-package overwrite.

Go migration tracker: https://github.com/WaylonWalker/markata-go/issues/1628
