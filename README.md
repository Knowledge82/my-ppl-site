# my-ppl-site

Static site backing **my-ppl.app** — the domain used by [My People](https://my-ppl.app)
(a mobile check-in app that lets people confirm they're okay and alerts a
small trusted circle if they don't).

This repo is intentionally minimal. It exists to serve two things over
plain HTTPS, both of which the Android OS and app stores fetch directly —
neither is meant to be browsed by humans:

- **`.well-known/assetlinks.json`** — Digital Asset Links verification
  file. Proves that `my-ppl.app` and the Android app share the same
  owner, so Android can hand `https://my-ppl.app/auth-callback` links
  (used for magic-link sign-in) directly to the app instead of opening
  them in a browser. See [Google's Digital Asset Links
  docs](https://developers.google.com/digital-asset-links) if you're
  curious how this works.
- **`privacy.html`** *(coming soon)* — the privacy policy required for
  the Google Play Store listing.

Nothing in this repo is sensitive: the fingerprint in `assetlinks.json`
is a public hash of the app's signing certificate, not a secret — it's
designed to be published openly. The actual app source lives in a
separate, private repository.
