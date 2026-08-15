# Publish as a shareable test PWA with GitHub Pages

This package is ready for GitHub Pages.

## One-time setup

1. Create a new GitHub repository, for example `GA-QNH`.
2. Upload the entire contents of this package to the repository's `main` branch.
3. In GitHub, open **Settings → Pages**.
4. Under **Build and deployment → Source**, select **GitHub Actions**.

The included workflow will deploy the app automatically.

When deployment finishes, GitHub will show a public HTTPS address similar to:

    https://YOUR-USERNAME.github.io/GA-QNH/

Send that HTTPS link to testers.

## Tester instructions

### iPhone / iPad
Open the link in Safari → Share → **Add to Home Screen**.

### Android
Open the link in Chrome → menu → **Add to Home screen** or **Install app**.

After the first successful load, the app's core files are cached for offline use.

## Updating the test build

Edit/replace the files in the repo and push to `main`.
GitHub Pages redeploys automatically.

Important: when changing cached app files, also change the cache name in
`service-worker.js` (for example `ga-climb-qnh-v3` → `ga-climb-qnh-v4`)
so installed devices pick up the new version cleanly.
