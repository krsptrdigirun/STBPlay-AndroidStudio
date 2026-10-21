# Host the matching privacy policy on GitHub Pages

The app retains its full policy offline in Settings → Privacy policy. Publishing a website is needed for the Console URL; the app does not need to open it.

## Free hosting

1. Sign into GitHub and create a public repository, for example `stbplay-privacy`. A GitHub Free account can use Pages from a public repository.
2. Upload **only** the contents of `publishing/privacy-site/` to the repository root. The required files are `index.html`, `privacy-policy.html` and `.nojekyll`. No Android source, keystore, logs or provider details belong in this repository.
3. Commit the files to the default branch, commonly `main`.
4. Repository Settings → Pages → Build and deployment → Deploy from a branch. Choose that branch and `/ (root)`, then Save.
5. Wait for GitHub's deployment to complete. Open the URL shown under Pages. A project site normally uses `https://YOUR-USERNAME.github.io/stbplay-privacy/`.
6. Enable Enforce HTTPS where available. Check the deployed page in a private browser window while signed out of GitHub. It must show the complete policy without login, cookies/consent walls or geographic restrictions. Do not submit a GitHub repository/blob/edit URL or a PDF URL.
7. Paste the public page URL into Play Console's Privacy policy field. Optionally record it in `publicPrivacyPolicyUrl` in `publishing.properties`; leave `privacyPolicyUrl=` blank to keep the app policy offline-only as requested.

## Keeping the app and page identical

The authoritative text is `app/src/main/assets/privacy_policy.txt`. Publisher/support tokens come from `publishing.properties`.

Run either:

```sh
./gradlew exportPrivacyPolicy
```

or, with Python 3:

```sh
python3 tools/export_privacy_policy.py
```

Both export the identical policy body to the two HTML files. After any policy edit, regenerate the website, build a new app version, and replace the deployed HTML. Do not edit just one copy.

The HTML has no JavaScript, forms, analytics, advertising, embedded resources or third-party fonts. Its CSS is inline. The policy discloses that GitHub itself logs visitor IP addresses for website security. The support email link opens the user's email client only when selected.

## Final checks

- Policy says STBPlay and LoopX Studio and contains the correct support email.
- Effective date and data practices match the app you are submitting.
- Page displays correctly on a phone and desktop, supports zoom and dark mode, and is printable.
- Both HTML routes return the policy, and HTTPS is valid.
- No provider passwords, real MAC identifiers, private playlist URLs, signing keys or logs appear in the repository.

Sources: [GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages), [HTTPS](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https), [Play privacy-policy requirements](https://support.google.com/googleplay/android-developer/answer/10144311).
