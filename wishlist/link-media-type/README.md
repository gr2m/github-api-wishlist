# Add link media type

Returns the value of the `Location` header for endpoints that would otherwise redirect.

## Why

In browsers, redirects are happening transparently. There is no way to access a redirect response, due to security concerns.

## Workarounds

This is not a problem in any environment but browsers. Any other environment can access the `Location` header of the `302` response. But even for these environments, it might be more convenient to retrieve the redirect location and maybe other meta information such as expiration of the download URL as a JSON response.

## Suggestions

### Option 1: enable CORS headers in adjacent domains

The best solution would be to [add CORS headers to all api.github-com-adjacent domains](../cors-for-adjacent-domains). That would allow to send `HEAD` requests which would follow the redirects without downloading response bodies. Browsers can read out `response.url` after the final redirect, if the `HEAD` request was successful.

### Option 2: add `link` media type

Add `link` to the list of existing [Media Type formats](https://developer.github.com/v3/media/).

A new section might look like this

````markdown
## Redirect links

A link media type format is supported for endpoints that respond with a 302 redirect, such as [Get archive link](https://developer.github.com/v3/repos/contents/#get-archive-link), [Download an artifact (Actions)](https://developer.github.com/v3/actions/artifacts/#download-an-artifact), or [Get a release asset](https://developer.github.com/v3/repos/releases/#get-a-single-release-asset).

### Link

```
application/vnd.github.VERSION.link
```

Returns the full redirect URL as text

```
application/vnd.github.VERSION.link+json
```

Returns a JSON response with a "location" key containing the full redirect URL as well as an `"expires_at"` key where applicable.
````

## Use case

- Retrieving the download link for GitHub repository archives or Release assets in browsers. See [octokit/rest.js#881](https://github.com/octokit/rest.js/issues/881)

---

[back](../..)
