# Emend

An offline AI proofreader that runs entirely in your browser via
[transformers.js](https://huggingface.co/docs/transformers.js). Nothing you
type is ever sent anywhere.

| Model | Size | Notes |
|---|---|---|
| Gemma 1B | ~860MB | General-purpose, all tones |
| Grammar (T5-small) | ~95MB | Dedicated grammar correction, Deep Fix only |

Both models download once (browser-cached after that) and run in a Web Worker.
A built-in rule-based engine (Harper) handles spelling and basic grammar
without needing the AI models at all.

## Try it

Open **[bootloader.html](https://cdn.jsdelivr.net/gh/Sm0keSkreen/Emend@main/bootloader.html)**.
It always loads the current version of the app straight from this repo via
jsDelivr's GitHub CDN, no build step or install required.

## How it works

`emendapp.html` is a single self-contained file (HTML/CSS/JS all inline).
jsDelivr serves `.html` files from GitHub as `text/plain`, so `bootloader.html`
fetches it as text and renders it via an iframe's `srcdoc`. It resolves the
current commit SHA through GitHub's API first, so it always gets the latest
push instead of a possibly-stale CDN edge cache of the `@main` branch alias.
