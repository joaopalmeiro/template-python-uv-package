# Template Notes

- https://docs.astral.sh/uv/guides/projects/
  - https://docs.astral.sh/uv/concepts/projects/init/
    - https://docs.astral.sh/uv/concepts/projects/init/#libraries
  - https://docs.astral.sh/uv/concepts/projects/dependencies/#development-dependencies
  - https://docs.astral.sh/uv/concepts/projects/config/
  - https://packaging.python.org/en/latest/guides/writing-pyproject-toml/
  - [change `uv version` to be an interface for project version reads and edits](https://github.com/astral-sh/uv/pull/12349)
  - https://docs.astral.sh/uv/reference/cli/#uv-version
- https://github.com/ninoseki/uv-dynamic-versioning
  - https://docs.python.org/3.10/library/importlib.metadata.html
  - https://versioningit.readthedocs.io/en/stable/runtime-version.html
  - https://github.com/astral-sh/uv/issues/8714#issuecomment-3034970864
- https://sarahglasmacher.com/how-to-build-python-package-uv/

## Commands

```bash
uv init --lib template-python-uv-package
```

```bash
uv run python -c "from template_python_uv_package import __version__; print(__version__)"
```
