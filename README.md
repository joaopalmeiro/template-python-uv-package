# template-python-uv-package

Opinionated Python + uv template for new packages.

## Development

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
echo "v$(uv version)" | pbcopy
```

- Commit and push changes.
- Create a tag on [GitHub Desktop](https://github.blog/2020-05-12-create-and-push-tags-in-the-latest-github-desktop-2-5-release/).
- Check [GitHub](https://github.com/joaopalmeiro/template-python-uv-package/tags).

```bash
hatch publish
```

- Check [PyPI](https://pypi.org/project/template-python-uv-package/).

```bash
uv publish
```
