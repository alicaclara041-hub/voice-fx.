# VOICE FX — live WhatsApp-call feasibility notes

Research checked on 12 November 2026 against official platform documentation.

## iPhone / iOS

Apple documents a microphone-injection feature available from iOS 18.2. It is designed for accessibility apps to add spoken audio (for example, synthesized speech) to supported calls. The user must enable **Settings → Accessibility → Audio & Visual → Add Audio in Calls**, and the app must request microphone-injection permission. The API sets an injection mode such as `spokenAudio`; Apple describes the result as app audio being added alongside microphone input.

This is not a documented API for taking the physical microphone stream, transforming it, and replacing WhatsApp's outgoing microphone stream. It may be useful for a separate accessibility-style audio-injection experiment, but it does not establish that VOICE FX can perform live voice conversion in WhatsApp. Compatibility with WhatsApp is not guaranteed and would require a native iOS prototype and device testing.

Official references:
- https://developer.apple.com/documentation/avfaudio/adding-synthesized-speech-to-calls
- https://developer.apple.com/documentation/avfaudio/avaudiosession/microphoneinjectionmode

## Android

Android's official audio-input-sharing documentation says that during a voice call, the call receives microphone input. An ordinary app cannot concurrently take that microphone input; Android identifies accessibility services and privileged/pre-installed apps as special cases. Capturing another app's playback is a separate Android feature and is limited by usage and capture policy; `VOICE_COMMUNICATION` audio is excluded from ordinary playback capture.

Therefore an ordinary third-party VOICE FX app cannot assume it can intercept and replace WhatsApp's live-call microphone audio. An accessibility service is not automatically a supported route for processing and reinjecting a transformed microphone stream. A privileged/system integration or WhatsApp-supported integration would be a different project and cannot be promised here.

Official references:
- https://developer.android.com/media/platform/sharing-audio-input
- https://developer.android.com/media/platform/av-capture
- https://developer.android.com/reference/android/media/AudioAttributes#ALLOW_CAPTURE_BY_ALL

## Current project decision

Keep the cross-platform recorder/effects/export path as the primary product. Treat live-call support as a research-only track until a specific, documented API path and a real WhatsApp device test demonstrate otherwise. Do not market or label live WhatsApp voice changing as supported.
