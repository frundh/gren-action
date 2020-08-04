# GitHub Release Notes Action

Publish changelog and release notes using [Gren](https://github.com/github-tools/github-release-notes).

## Usage

Configure Gren usign `.grenrc` in your repository and run this action in GitHub actions workflow:

```yaml
name: Release notes

on: [release]
  types: [published]
    
jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: lakto/gren-action@v1.1.0
        env:
          GITHUB_TOKEN: ${{ secrets.GH_TOKEN }}
        with:
          options: --override --prerelease 
```
