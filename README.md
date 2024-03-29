# Publish gem Github Action

An action that builds and then publishes a Ruby gem to [rubygems.org](https://rubygems.org) or GitHub Packages.

Will find every `.gemspec` file in current directory and publish a gem for it.

Runs on `ubuntu` and `macos`.

## Usage

```yaml

---
name: Build and Publish GEM

on:
  push:
    tags:
      - '*'

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - name: checkout
        uses: actions/checkout@v1
      - name: Publish gem
        uses: yousysadmin/action-publish-gem@v1
        with:
          # Optional, will publish to RubyGems if specified
          api_key: ${{secrets.RUBYGEMS_API_KEY}}
          # Optional, will publish to GitHub Packages if specified
          github_token: ${{secrets.GITHUB_TOKEN}}
```

> It is possible to publish both to RubyGems and GitHub Packages
