# Enable CORS for adjacent domains

Domains such as `uploads.github.com`, `codeland.github.com`, `pipelines.actions.githubusercontent.com`, and GitHubs `*.s3.amazonaws.com` should have the same CORS settings as `api.github.com`

## Why

Several REST API endpoints are currently unusable for browsers due to the usage of different domains and their CORS settings. The same APIs work on GitHub Enterprise Server where the domain remains the same in most cases.

## Workarounds

There are no possible workarounds due to the browser's security model.

## Use case

- Upload/Download a release asset (See [octokit/rest.js#758](https://github.com/octokit/rest.js/issues/758))
- Download a repository archive (See [octokit/rest.js#758](https://github.com/octokit/rest.js/issues/758))
- [Get raw-log URL for GitHub Action run](https://github.com/octokit/rest.js/discussions/1805)

---

[back](../..)
