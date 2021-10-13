# GitHub Release Notes Action

Publish changelog and release notes using [Gren](https://github.com/github-tools/github-release-notes).

## Usage

Configure Gren usign `.grenrc` in your repository and run this action in GitHub actions workflow:

```yaml
name: Release notes

on: 
  release:
    types: [published]

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - 
        name: Checkout
        uses: actions/checkout@v2
      - 
        name: Create Release
        uses: frundh/gren-action@v2.1.0
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          command: release
          options: '--override --prerelease'
      - 
        name: Update CHANGELOG.md
        uses: frundh/gren-action@v2.1.0
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          command: changelog
          options: '--override'
```

In options you can add all [options from Gren](https://github-tools.github.io/github-release-notes/options.html) itself except of `--username`, `--repo` and `--token`. They are already part of the lakto/gren-action entrypoint script.
