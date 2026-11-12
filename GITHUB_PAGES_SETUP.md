# Publish VOICE FX with GitHub Pages

This package is a browser-based Progressive Web App (PWA), not an APK, IPA, or native app.

## Publish
1. Sign in to GitHub and create a new **public** repository named `voice-fx` (or another name you prefer).
2. Upload the **contents** of this folder to the repository's top level. Make sure `index.html` is at the repository root, not inside another folder.
3. In the repository, open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Choose branch `main` and folder `/(root)`, then save.
6. Wait for GitHub Pages to publish. Open the URL shown in Settings → Pages.

## On iPhone
1. Open the published HTTPS URL in Safari.
2. Tap the Record button and allow microphone access when prompted.
3. To add an icon, use Safari's Share menu → Add to Home Screen.

## On Android
1. Open the published HTTPS URL in Chrome.
2. Allow microphone access when prompted.
3. Use Chrome's Install app / Add to Home screen option if offered.

## Important
- GitHub Pages hosting makes the PWA accessible over HTTPS; it does not turn it into a native iOS or Android app.
- The app processes recordings locally in the browser. Do not upload private recordings to public repositories.
- Real-device microphone, playback, sharing, and install tests are still required.
- The current build does not replace the microphone in WhatsApp live calls.
