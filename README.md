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

The contact address is `delakrua8@gmail.com`, in both pages, in both languages.

## Published at

```
https://delakrua8-rgb.github.io/lumi-site/              Support URL
https://delakrua8-rgb.github.io/lumi-site/privacy.html  Privacy Policy URL
```

GitHub Pages, from the public `lumi-site` repository — separate from this one on purpose:
this repository is private and holds the app's source, and publishing the policy must not
mean publishing everything else.

## Updating

This folder is the source of truth. Edit here, commit, then publish the folder alone:

```bash
git subtree push --prefix=site site main
```

Editing here rather than in the published repository is what keeps the policy and the code
it describes changing in the same commit. A privacy policy that has drifted from the code
is worse than none at all: it is a false statement rather than a missing one.
