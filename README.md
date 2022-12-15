# action-bumpr-go

<p align="center">
  <a href="https://github.com/PackagrIO/docs">
  <img width="300" alt="portfolio_view" src="https://github.com/PackagrIO/bumpr/raw/master/images/bumpr.png">
  </a>
</p>

Github Action that allows you to bump SemVer version for Go repositories

# Documentation
Full documentation is available at [PackagrIO/docs](https://github.com/PackagrIO/docs)

# Usage

```yaml
name: Release
# This workflow is triggered manually
on:
  workflow_dispatch:
    inputs:
      version_bump_type:
        description: 'Version Bump Type (major, minor, patch)'
        required: true
        default: 'patch'
jobs:
  build:
    name: Build
    runs-on: ubuntu-latest
    container: golang
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Bump version
        id: bump_version
        uses: packagrio/action-bumpr-node@master
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          version_bump_type: ${{ github.event.inputs.version_bump_type }}
          github_token: ${{ secrets.GITHUB_TOKEN }}
```

# Inputs

- `version_bump_type`
- `version_metadata_path`

# Outputs

- `release_version`
