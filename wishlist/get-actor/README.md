# Get /actor

Returns the means of authentication to access it. Returns list of permissions if applicable

## Why

When a tool is agnostic to the used authentication strategy, it is currently impossible to find out what kind of authentication is being used, and to verify if all required permissions are set. But verifying authentication is important to such tools in order to give its users helpful error messages.

## Workarounds

The are ways to find out what authentication is being used, but they all required more than one request.

And for installation access tokens, it is currently not possible to retrieve its given permissions.

## Use case

- semantic-release: find out if the provided `GITHUB_TOKEN` has all required permissions to create a GitHub release and to comment on and add labels to issues and pull requests. See [semantic-release/github#272](https://github.com/semantic-release/github/pull/272)

---

[back](../..)
