# actions-poetry

![Starts in 2024](https://img.shields.io/badge/Started-2024-brightgreen)

GitHub Action for Python projects using [poetry](https://github.com/python-poetry/poetry).

## Getting started

### Create your workflow

```yaml
name: CI
on: 
  push:
    branches: [main]

jobs:
  ci:
    strategy:
      fail-fast: false
      matrix:
        python-version: ["3.8", "3.9", "3.10", "3.11"]
        poetry-version: ["1.6.1", "1.7.1"]
        os: [ubuntu-22.04, macos-latest, windows-latest]
    runs-on: ${{ matrix.os }}
    steps:
      - uses: actions/checkout@v4
      - name: Install python & poetry
        uses: zikoengxi/actions-poetry@v1
        with:
          python-version: ${{ matrix.python-version }}
          poetry-version: ${{ matrix.poetry-version }}
      - name: Poetry --help
        run: poetry --help
```

Input parameters:

- python-version(required): The version of python to install.
- poetry-version(optional): The version of poetry to install. The default value is 'latest'.
- poetry-plugins(optional): The whitespace/newline separated list of poetry plugins to install.

## License

[MIT](LICENSE)
