# VOICE FX v0.2.1 test report

Run date: 12 November 2026

## Passed
- iOS Safari metadata is present (`apple-mobile-web-app-capable`, status-bar style, app title).
- Preview audio uses `playsinline` to avoid forced full-screen playback behavior on iPhone.
- Recording start control is disabled before awaiting the microphone permission prompt, preventing duplicate permission requests.
- JavaScript syntax check for the page's inline script (`node --check`).
- JavaScript syntax check for `sw.js` (`node --check`).
- HTML parser check: no duplicate element IDs; all required recording and playback controls exist.
- `manifest.webmanifest` parses as JSON and includes both 192 px and 512 px icons.
- WAV encoder smoke tests: RIFF/WAVE headers, PCM16 format, sample rate, data length, clipping endpoints, stereo output, and unsupported-channel rejection.
- Mock-Web-Audio smoke tests: Natural, Deep, High, Robot, Echo and Radio each build the expected processing branch and return a WAV blob. Deep/High output-length calculations and Echo tail calculation are checked.
- ZIP archive integrity check.

## Not passed / not performed
- Real microphone capture and recording in Safari on iPhone.
- Real microphone capture and recording in Chrome on Android.
- Actual sound-quality listening tests for the six effects.
- Real Web Share sheet / WhatsApp file attachment test.
- PWA installation and offline relaunch on physical devices.
- Live WhatsApp-call injection or voice conversion.

The audio-engine smoke tests use mocked Web Audio nodes. They verify control flow, graph construction and WAV packaging, not the actual sound produced by a phone's audio engine. A headless Chromium attempt in this environment did not complete, so no browser-level result is claimed.
