actions-couscous
===
[![release](https://img.shields.io/github/release/BilelJegham/actions-couscous.svg)](https://github.com/BilelJegham/actions-couscous/releases/latest)
[![license](https://img.shields.io/github/license/BilelJegham/actions-couscous.svg)](https://github.com/BilelJegham/actions-couscous/blob/master/LICENSE)

[![Couscous Artefact](https://github.com/BilelJegham/actions-couscous/workflows/Couscous%20Artefact/badge.svg)]() [![Couscous GithubPage](https://github.com/BilelJegham/actions-couscous/workflows/Coucous%20GithubPage/badge.svg)]()


## Getting started

Add your workflow file, the following step
```yml
  - uses: `BilelJegham/actions-couscous@v0`
```

## Example

### Publish on GithubPage

```yml
name: Couscous GithubPage

on:
  push:
    branches:
      - master

jobs:
  deploy:
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@v1

      - uses: `BilelJegham/actions-couscous@v0`
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./.couscous/generated
```



### Artefact 
Generate zip artefact with the generate website.
```yml
name: Couscous Artefact

on:
  push:
    branches:
      - master

jobs:
  deploy:
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@v1

      - uses: `BilelJegham/actions-couscous@v0`

      - name: Upload artifact
        uses: actions/upload-artifact@v1.0.0
        with:
          # Artifact name
          name: Couscous
          # Directory containing files to upload
          path: .couscous/generated

```