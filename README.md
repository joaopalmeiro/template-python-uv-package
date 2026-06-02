# template-python-uv-package

[![uv](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/uv/main/assets/badge/v0.json)](https://github.com/astral-sh/uv)
[![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)
[![Checked with mypy](https://www.mypy-lang.org/static/mypy_badge.svg)](https://mypy-lang.org/)

Opinionated [Python](https://www.python.org/) + [uv](https://github.com/astral-sh/uv) template for new packages.

- [Source code](https://github.com/joaopalmeiro/template-python-uv-package)
- [PyPI package](https://pypi.org/project/template-python-uv-package/)
- [ClickPy](https://clickpy.clickhouse.com/dashboard/template-python-uv-package)
- [ecosyte.ms](https://packages.ecosyste.ms/registries/pypi.org/packages/template-python-uv-package)
- [Libraries.io](https://libraries.io/pypi/template-python-uv-package)
- [Open Source Insights](https://deps.dev/pypi/template-python-uv-package)
- [OSV](https://osv.dev/list?q=template-python-uv-package&ecosystem=PyPI)
- [PePy](https://pepy.tech/projects/template-python-uv-package)
- [PyPack Trends](https://pypacktrends.com/?packages=template-python-uv-package&time_range=allTime)
- [PyPI Stats](https://pypistats.org/search/template-python-uv-package)
- [Snyk](https://security.snyk.io/package/pip/template-python-uv-package)
- [Socket](https://socket.dev/pypi/package/template-python-uv-package)

## Getting Started

1. Go to or create the package folder.
2. Get the template files:

```bash
npx giget@3.2.0 github:joaopalmeiro/template-python-uv-package . --force
```

3. Search for `template-python-uv-package` and replace it with the package name. Ignore the template repository URL in the [NOTES.md](NOTES.md) file.
4. Search for `template_python_uv_package` and replace it with the underscored version of the package name.
5. Search for `Opinionated [Python](https://www.python.org/) + [uv](https://github.com/astral-sh/uv) template for new packages.`/`Opinionated Python + uv template for new packages.` and replace it with the (short) package description.
6. Search for `João Palmeiro` and replace it with the author's name.
7. Search for `joaopalmeiro@proton.me` and replace it with the author's email address.
8. Update the `Source code` link at the top to the package repository link (if necessary).
9. Change `GitHub` in the [`Deployment`](#deployment) section to `GitLab` or `Codeberg` and update the link to the corresponding Tags page (if necessary).
10. Update the `Issues` and `Source` fields in the [pyproject.toml](pyproject.toml) file with their respective repository-related links (if necessary).
11. Delete the [TEMPLATE.md](TEMPLATE.md) file.
12. Delete the [`Getting Started`](#getting-started) section.

## Development

Install [uv](https://docs.astral.sh/uv/getting-started/installation/), [1Password](https://1password.com/downloads/), and [1Password CLI](https://developer.1password.com/docs/cli/get-started/) (if necessary):

```bash
curl -LsSf https://astral.sh/uv/0.11.6/install.sh | sh
```

```bash
uv python install
```

```bash
uv audit --verbose
```

```bash
uv run python -c "from template_python_uv_package import __version__; print(__version__)"
```

```bash
uv run mypy
```

```bash
uv run ruff format
```

```bash
uv run ruff check --fix
```

## Deployment

```bash
uv version --bump patch
```

```bash
uv version --bump minor
```

```bash
uv version --bump major
```

```bash
uv build
```

```bash
echo "v$(uv version --short)" | pbcopy
```

- Commit and push changes.
- Create a tag on [GitHub Desktop](https://github.blog/2020-05-12-create-and-push-tags-in-the-latest-github-desktop-2-5-release/).
- Check [GitHub](https://github.com/joaopalmeiro/template-python-uv-package/tags).

```bash
UV_PUBLISH_TOKEN="op://Development/PyPI/UV_PUBLISH_TOKEN" op run -- uv publish
```

- Check [PyPI](https://pypi.org/project/template-python-uv-package/).
