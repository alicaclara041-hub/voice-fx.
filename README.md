# VOICE FX v0.2.1 — cross-platform voice-note prototype

## Included files
- `index.html` — recording interface and on-device audio-effects engine.
- `manifest.webmanifest` — installable web-app metadata and icons.
- `sw.js` — versioned service worker with app-shell caching.
- `icon-192.png`, `icon-512.png` — app icons.

## Implemented in v0.2.1 (includes the v0.2 foundation)
- iOS home-screen metadata and inline audio playback hints for Safari.
- Recording button is locked while the iOS/Android microphone permission prompt is pending, preventing duplicate microphone requests.
- Microphone recording through `getUserMedia` and `MediaRecorder`.
- A 60-second recording limit, elapsed-time display, empty-recording check, microphone error handling, and track cleanup.
- On-device decoding and rendering through Web Audio / OfflineAudioContext.
- Natural, Deep, High, Robot, Echo and Radio effects.
- WAV export and Web Share API file sharing when the browser supports file sharing.
- Releasing old audio object URLs when recordings/effects change.
- PWA manifest icons and versioned offline app-shell cache.

## Known limits
- Deep and High use playback-rate pitch changes, so they also change duration. They are not formant-preserving pitch shifting.
- Robot is a basic amplitude-modulated effect, not an AI voice conversion model.
- Sharing may create an ordinary audio-file attachment in WhatsApp, not its native voice-note bubble.
- This app does not change the microphone signal inside WhatsApp live calls.
- Physical iPhone and Android testing has not yet been completed.

## Run / test

For iPhone, use current Safari over HTTPS. If added to the Home Screen, launch VOICE FX from its icon; Safari may still require a microphone permission prompt on first use. Keep the app in the foreground during recording for this prototype.

Run the included deterministic audio-engine smoke tests with Node.js:

```sh
node tests/audio-engine-smoke.cjs
```

The tests use mocked Web Audio nodes; they do not replace real-phone listening tests. See `TEST_REPORT.md` and `LIVE_CALL_RESEARCH.md` for the current verification record and call-platform findings.

1. Host this folder on an HTTPS origin. `localhost` is also treated as a secure context for local development.
2. Open the HTTPS page in current Safari on iPhone or Chrome on Android.
3. Tap **Start recording** and allow microphone access.
4. Record 5–10 seconds, then tap **Stop** (the app automatically stops at 60 seconds).
5. Select an effect, tap **Apply effect to recording**, preview the WAV, then save or share it.
6. To install, use **Add to Home Screen** in Safari or the browser's **Install app** option on Android.

## Permissions / privacy
- The browser will ask for microphone permission when recording starts.
- No account, backend, or audio upload is used by this prototype. Processing is local in the browser.
- The service worker and microphone require HTTPS when hosted publicly.
