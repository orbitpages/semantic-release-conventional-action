# semantic-release-action

A GitHub action for package release workflow with [semantic-release](https://github.com/semantic-release/semantic-release) and [conventionalcommits](https://www.conventionalcommits.org/pt-br/)

## Usage

```yml
permissions:
  contents: read
  issues: write
  pull-requests: write

- name: Release Package
  uses: orbitpages/semantic-release-action@main
```

Add file `.releaserc` at root repository with semantic-release configuration

Ex:

```json
{
  "branches": [
    "main",
    {
      "name": "dev",
      "prerelease": "beta",
      "channel": "beta"
    }
  ],
  "preset": "conventionalcommits",
  "plugins": [
    "@semantic-release/commit-analyzer",
    "@semantic-release/release-notes-generator",
    [
      "@semantic-release/exec",
      {
        "verifyReleaseCmd": "echo ${JSON.stringify(nextRelease)} > version"
      }
    ]
  ]
}
```

## Default plugins

These four plugins are already part of `semantic-release-action`. They do not have to be installed separately:

```text
"@semantic-release/commit-analyzer"
"@semantic-release/release-notes-generator"
"@semantic-release/npm"
"@semantic-release/github"
"@semantic-release/exe"
```
