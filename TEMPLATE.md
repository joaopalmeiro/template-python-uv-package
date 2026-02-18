# Template Notes

- https://docs.astral.sh/uv/guides/projects/
  - https://docs.astral.sh/uv/concepts/projects/init/
    - https://docs.astral.sh/uv/concepts/projects/init/#libraries
  - https://docs.astral.sh/uv/concepts/projects/dependencies/#development-dependencies
  - https://docs.astral.sh/uv/concepts/projects/config/
  - https://packaging.python.org/en/latest/guides/writing-pyproject-toml/
  - [change `uv version` to be an interface for project version reads and edits](https://github.com/astral-sh/uv/pull/12349)
  - https://docs.astral.sh/uv/reference/cli/#uv-version
    - https://github.com/astral-sh/uv/releases/tag/0.7.0
  - https://github.com/astral-sh/uv/releases/tag/0.7.19
    - "The uv build backend is now stable, and considered ready for production use."
    - https://docs.astral.sh/uv/concepts/build-backend/
- https://github.com/ninoseki/uv-dynamic-versioning
  - https://docs.python.org/3.10/library/importlib.metadata.html
  - https://versioningit.readthedocs.io/en/stable/runtime-version.html
  - https://github.com/astral-sh/uv/issues/8714#issuecomment-3034970864
- https://sarahglasmacher.com/how-to-build-python-package-uv/
- https://docs.astral.sh/uv/getting-started/installation/#uninstallation
- [✨ How to define custom commands like `tool.rye.scripts`](https://github.com/astral-sh/uv/issues/6302)
  - https://github.com/phihung/tomlscript
  - https://mise.jdx.dev/
- [Using `uv run` as a task runner](https://github.com/astral-sh/uv/issues/5903)
  - https://github.com/taskipy/taskipy
  - https://github.com/nat-n/poethepoet
- [Snyk Advisor](https://snyk.io/advisor/python/template-python-uv-package)

## Commands

```bash
uv init --lib template-python-uv-package
```

```bash
uv lock --check
```

```bash
uv lock --dry-run
```

```bash
uv sync
```

## Snippets

```toml
[build-system]
requires = ["hatchling==1.27.0"]
build-backend = "hatchling.build"
```
