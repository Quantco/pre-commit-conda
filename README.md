# pre-commit-conda GitHub Action

## Overview

`pre-commit-conda` is a fork of the `pre-commit/action`. This GitHub Action runs pre-commit hooks in a conda environment managed by micromamba.

## Features

- Customizable Python version.
- Optional custom `condarc-file`.
- Caches pre-commit environment.

## Usage

Create `.github/workflows/pre-commit.yml` in your repository. Here's a quick template:

```yaml
name: pre-commit

on:
  pull_request:
  push:
    branches: [main]

jobs:
  pre-commit:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Run pre-commit with Conda
      uses: quantco/pre-commit-conda@v1
      with:
        extra-args: '--all-files' # Optional extra arguments (default: --all-files)
        condarc-file: '' # Optional custom condarc file (default: no custom condarc_file)
        python-version: '3.11' # Optional Python version (default: 3.11)
```

## Customizations

- `extra-args`: Specify single hook id or options for `pre-commit run`.
- `condarc-file`: Path to custom condarc file.
- `python-version`: Specify Python version.
