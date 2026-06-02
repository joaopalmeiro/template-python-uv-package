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
- "8. Open the [pyproject.toml](pyproject.toml) file and add the package-specific dependencies. See the [`Managing dependencies`](https://docs.astral.sh/uv/concepts/projects/dependencies/) page in the uv documentation for more information (if necessary)."
- `"License :: OSI Approved :: MIT License"`
- https://docs.pypi.org/trusted-publishers/
  - https://docs.pypi.org/trusted-publishers/security-model/
    - "Use a dedicated environment: GitHub Actions supports "environments," which can be used to isolate secrets to specific workflows. OIDC publishing doesn't use any pre-configured secrets, but a dedicated `publish` or `deploy` environment is a general best practice. Dedicated environments allow for additional protections like required reviewers, which can be used to require manual approval for a workflow using the environment."
    - https://docs.github.com/en/actions/how-tos/deploy/configure-and-manage-deployments/manage-environments#required-reviewers
    - "Limit the scope of your publishing job: your publishing job should (ideally) have only two steps:"
      - "Retrieve the publishable distribution files from a separate build job;"
      - "Publish the distributions using `pypa/gh-action-pypi-publish@release/v1`."
  - https://docs.pypi.org/trusted-publishers/adding-a-publisher/
- https://github.com/zizmorcore/zizmor/
- https://github.com/lirantal/pypi-security-best-practices
- https://github.com/suzuki-shunsuke/pinact
  - https://github.com/suzuki-shunsuke/pinact/issues/925
  - https://github.com/pypa/gh-action-pypi-publish/releases
- https://docs.astral.sh/uv/guides/integration/github/
  - https://docs.astral.sh/uv/guides/integration/github/#publishing-to-pypi
    - https://github.com/astral-sh/trusted-publishing-examples
      - `# Create this environment in the GitHub repository under Settings -> Environments`
- https://github.com/astral-sh/attest-action
- https://docs.astral.sh/uv/guides/package/#uploading-attestations-with-your-package
  - "`uv publish` does not currently generate attestations; attestations must be created separately before publishing."
  - https://github.com/astral-sh/uv/issues/15618
- https://docs.pypi.org/attestations/producing-attestations/
  - https://github.com/actions/attest
  - https://github.com/pypa/gh-action-pypi-publish
  - https://packaging.python.org/en/latest/guides/publishing-package-distribution-releases-using-github-actions-ci-cd-workflows/
- https://github.com/actions/download-artifact

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

```bash
source .venv/bin/activate
```

```bash
deactivate
```

```bash
rm -rf .mypy_cache/ .ruff_cache/ .venv/ dist/ src/template_python_uv_package/__pycache__/
```

## Snippets

```toml
[build-system]
requires = ["hatchling==1.27.0"]
build-backend = "hatchling.build"
```

```yaml
# .github/workflows/release.yml
name: Release

on:
  push:
    tags:
      - "v*"

permissions: {}

jobs:
  build:
    runs-on: ubuntu-latest
    permissions:
      contents: read

    steps:
      - uses: actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4.2.2

      - name: Install uv
        uses: astral-sh/setup-uv@d4b2f3b6ecc6e67c4457f6d3e41ec42d3d0fcb86 # v5.4.2

      - name: Build
        run: uv build

      - name: Upload dist
        uses: actions/upload-artifact@v4

        with:
          name: dist
          path: dist/

  publish:
    needs: build
    runs-on: ubuntu-latest
    permissions:
      contents: read
      id-token: write
      attestations: write

    steps:
      - name: Download dist
        uses: actions/download-artifact@v4
        with:
          name: dist
          path: dist/

      - name: Publish to PyPI
        uses: pypa/gh-action-pypi-publish@7f25271a4aa483500f742f9492b2ab5648d61011 # v1.12.4
```

```markdown
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
```
