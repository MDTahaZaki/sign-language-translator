# CogniSign — browser demo

Teach your own signs to the webcam, then sign sentences that are spoken aloud in
English, Hindi or Kannada. Everything runs in the browser; no video leaves the machine.

Based on the [Alexa sign language translator](https://github.com/shekit/alexa-sign-language-translator)
(KNN image classifier on SqueezeNet features), with the CogniSign interface and speech layer.

## Running

```
npm install
npm start
```

Open [`http://localhost:9966`](http://localhost:9966) in **Chrome** and allow the camera
(and the microphone, for the speech features).

`npm run build` regenerates `dist/build.js` after editing `main.js`.

## Using it

1. **Train** — start the camera, then hold **Record** next to each word while performing
   its sign (30+ examples each). Record **IDLE** with your hands down so the model knows
   when you are not signing. Add your own words at any time; type them in Devanagari or
   Kannada script to have them spoken in that language.
2. **Sign → Speech** — detected words appear as chips. A word is accepted at ≥90%
   confidence held for 3 frames; holding IDLE for 1.5s ends the sentence and speaks it.
   Optionally listen for a spoken reply afterwards (e.g. from an Amazon Echo).
3. **Speech → Text** — live transcription (en-IN / hi-IN / kn-IN) for a deaf or
   hard-of-hearing reader, plus type-to-speak.
4. **Model** — vocabulary, example counts, and which voices are installed.

## Notes

- Speech recognition only works in Chrome and needs an internet connection.
- Voices come from the OS/browser. If a language shows ✗ on the Model tab, install it in
  Windows Settings → Time & language → Speech, then restart Chrome.
- Training is held in memory; reloading the page clears it.
