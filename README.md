# Reframe

Write down a harsh thought, get kinder words back, then rest with them during a quiet binaural-beat session.

**Live demo:** https://farfuturesolutions.com/reframe/

Reframe is a single self-contained `index.html`. It has no build step, no dependencies, no server, no accounts, and no analytics. To run it locally, open `index.html` in a browser.

## What it does

1. **You type one or more negative thoughts**, one per line (for example "I'm not good enough" or "nobody cares about me").
2. **It suggests kind words.** Each thought becomes 2 to 4 short, present-tense affirmations written to "you", such as "You are worthy." or "People care about you." You can edit, remove, or add lines.
3. **You listen.** A session plays a binaural beat over soft noise, and your affirmations are spoken quietly underneath.

## How it works

### Rule-based, offline reframing
The reframing is plain JavaScript keyword and pattern matching. There is no AI model and no network call. Each thought is checked against these themes: worth, existence and belonging, love, care and loneliness, failure and competence, fear and anxiety, shame, hopelessness, body image, and life and safety. A thought can match more than one theme, and the replies are drawn from each one it matches. If nothing matches, it uses a gentle general set. Duplicate lines are removed.

### Binaural beats (Web Audio API)
- The left ear gets a 400 Hz sine tone and the right ear gets 400 Hz plus the beat: theta 4 Hz, theta 6 Hz, or alpha 10 Hz.
- Under the tones is a looping brown-noise bed, low-pass filtered so it sounds soft, like rain.
- Sessions run 10, 15, or 20 minutes, with a 20-second fade in and a 25-second fade out. You get a master volume, a noise level, and pause, resume, and stop buttons.
- The audio context starts and resumes from a tap, so it works with Safari on iOS. Headphones are required, because the beat only forms when each ear hears its own tone.

### Quiet spoken affirmations (Web Speech API)
- The device's built-in voice (`speechSynthesis`) reads the affirmations one at a time, with a 2.5-second gap between them, looping for the whole session.
- *Whisper* mode sets `utterance.volume` low (about 0.12 by default), and *Audible* mode makes the words clear. A slider adjusts the level.
- Browsers can't route speechSynthesis through Web Audio, so the words play alongside the tones instead of being mixed into them. Some browsers, notably Safari on iOS, ignore `utterance.volume`.
- Evidence that subliminal audio changes how people think is limited. What clearly helps is relaxing and hearing kind, specific words often. The page says this plainly.

### Optional WAV download
The page can render the tones and noise into a stereo 16-bit WAV at 22,050 Hz, in the browser, so you can listen offline. Spoken words aren't included, because a browser can't record its own speech output.

## Privacy
Nothing you type leaves your browser. The page makes no network requests. It has no tracking or analytics, and it doesn't save your thoughts, not even in local storage. The one external link is to findahelpline.com in the safety card, and it opens only if you tap it.

## Safety
If a thought matches self-harm or suicide language, the page shows a gentle card above the results. It never blocks you from continuing. The card says:

> You're not alone. If you're thinking about ending your life, you can call or text **988** (Suicide & Crisis Lifeline, US) any time, or find a line in your country at [findahelpline.com](https://findahelpline.com).

Reframe is a relaxation tool, not medical or mental-health care, and it is no substitute for professional help. Don't use it while driving or doing anything that needs your attention. If you have epilepsy or a seizure disorder, check with a doctor before using pulsing audio. Keep the volume moderate.

## License
MIT. See [LICENSE](LICENSE).
