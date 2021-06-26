# A github action for creating PDFs from github markdown

his action creates PDF documents from github markdown

## Inputs

### `markdown_dir`

**Required** Location of markdown files in github repository. Default `doc`.

### `output_dir`

**Required** Location to output PDF files to. Default `tmp`.

## Example usage

![Alt text](https://interactive-examples.mdn.mozilla.net/media/cc0-images/grapefruit-slice-332-332.jpg "a title")

```
on:
  push:
    paths:
      - 'doc/**'

name: CreatePDFs

jobs:
  makepdfs:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v1
    - uses: mkrakowitzer/actions-makepdfs@master
      if: github.ref == 'refs/heads/master'
      with:
        markdown_dir: doc
        output_dir: tmp
    - uses: actions/upload-artifact@v1
      with:
        name: platform-architecture-docs
        path: tmp
```
