Action-couscous
===
[![release](https://img.shields.io/github/release/BilelJegham/action-couscous.svg)](https://github.com/BilelJegham/action-couscous/releases/latest)
[![license](https://img.shields.io/github/license/CouscousPHP/GitHub-Action.svg)](https://github.com/CouscousPHP/GitHub-Action/blob/master/LICENSE)

![Couscous Artefact](https://github.com/CouscousPHP/GitHub-Action/workflows/Couscous%20Artefact/badge.svg) 
![Couscous GithubPage](https://github.com/CouscousPHP/GitHub-Action/workflows/Couscous%20GithubPage/badge.svg)

Couscous turns Markdown documentation into websites. http://couscous.io/

This is a GitHub Action to generate couscous websites. View : https://couscousphp.github.io/GitHub-Action/


## Getting started

Add your workflow file, the following step
```yml
  - uses: CouscousPHP/GitHub-Action@v1
```

## Examples

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

      - uses: CouscousPHP/GitHub-Action@v1
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./.couscous/generated
```



### Artefact zip
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

      - uses: CouscousPHP/GitHub-Action@v1

      - name: Upload artifact
        uses: actions/upload-artifact@v1.0.0
        with:
          # Artifact name
          name: Couscous
          # Directory containing files to upload
          path: .couscous/generated

```

## License
Couscous is released under the MIT License.
