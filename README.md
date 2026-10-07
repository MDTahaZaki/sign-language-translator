# CogniSign — browser demo

Two-way sign language demo that runs entirely in the browser:

- **Sign → Speech** — teach your own signs to the webcam, then sign sentences that are
  spoken aloud in English, Hindi or Kannada.
- **Text → Sign** — type or say a sentence and a 3D avatar signs it, fingerspelling
  anything outside its dictionary.
- **Speech → Text** — live captions of what a hearing person says.

No video leaves the machine. Based on the
[Alexa sign language translator](https://github.com/shekit/alexa-sign-language-translator)
(KNN classifier on SqueezeNet features), with the CogniSign interface and speech layer.

## Running

Double-click **`start-demo.bat`** (installs on first run, then opens the browser), or:

```
npm install
npm start
```

Open [`http://localhost:9966`](http://localhost:9966) in **Chrome** and allow the camera
and microphone. `npm run build` regenerates `dist/build.js` after editing `main.js`;
`avatar.js` is loaded directly and needs no build.

## Using it

1. **Train** — start the camera, then hold **Record** next to each word while performing
   its sign (30+ examples each). Record **IDLE** with your hands down. Training is saved
   in the browser and restored after a reload; **Reset all training** (click twice) clears it.
2. **Sign → Speech** — a word is accepted at ≥90% confidence held for 3 frames; holding
   IDLE for 1.5s ends the sentence and speaks it. Optionally listen for a spoken reply.
3. **Text → Sign** — 38-sign dictionary (greetings, questions, needs, places, NAMASTE…),
   English plus common Hindi/Kannada words. Helper words (is, the, a…) are dropped;
   other English words are fingerspelled. Drag the avatar to turn it.
4. **Speech → Text** — transcription in en-IN / hi-IN / kn-IN; "Sign this" sends it to the avatar.
5. **Model** — vocabulary, example counts, installed voices.

## Offline

The SqueezeNet weights (`weights/`) and three.js (`vendor/three/`) are bundled, so sign
recognition, training and the avatar work without internet. Speech recognition (Chrome's)
needs internet; the web fonts fall back to system fonts.

## Notes

- Avatar signs are illustrative approximations, not validated by a native ISL signer.
- If a language shows ✗ on the Model tab, install its voice in Windows Settings →
  Time & language → Speech, then restart Chrome.
- Third-party licences: three.js (MIT, `vendor/three/LICENSE`).
