# site/

The two pages App Store Connect will not let the app be submitted without: a **privacy
policy** (guideline 5.1.1, and 5.1.3 for health apps) and a **support page**. Both are
required, both must be publicly reachable without a login, and an empty support page with
only an email address has been rejected before — so this one answers real questions.

Three static files, no build step, no external requests. That last part is deliberate: a
privacy policy that pulls a font from a third-party CDN contradicts itself on the first
request.

```
index.html     support   →  App Store Connect ▸ Support URL
privacy.html   policy    →  App Store Connect ▸ Privacy Policy URL
style.css      shared
```

## Before publishing

Replace `ПОЧТА@example.com` — two places in each page:

```bash
grep -rn "ПОЧТА@example.com" site/
```

## Publishing

Anywhere that serves static files. GitHub Pages is free and its `github.io` URLs are
accepted by Apple:

1. A **new, separate, public** repository — `lumi-site` or similar. Separate on purpose:
   this repository holds the app's source, and publishing the policy must not mean
   publishing everything else.
2. Copy the contents of this folder into it and push.
3. Settings ▸ Pages ▸ Source: `main`, folder `/ (root)`.
4. The URLs become `https://<account>.github.io/lumi-site/` and `…/privacy.html`.

Keep this folder as the source of truth and copy from it, so the published policy and the
app that the policy describes are changed in the same commit. A privacy policy that has
drifted from the code is worse than none at all — it is a false statement rather than a
missing one.
