# Pixel & Blur (Guess the Pixel)

A browser quiz game for team events: a famous face starts heavily pixelated, blurred and grayscale and sharpens
step by step while the available points drop. Teams shout "Stop!" and answer; the earlier you guess, the more you score.
Built as a single `index.html` for a projector, with a bilingual Kazakh / Russian interface.

## Features

- 10-step reveal on `<canvas>`: pixelation (downscale/upscale without smoothing) plus CSS `blur()` and `grayscale()`;
  points go 1000 → 100.
- Solo mode or 2–6 teams with editable names; host picks the answering team by button or keys 1–6.
- Answer checking that forgives case, punctuation, ё/е, Kazakh letters and 1–2 typos, and rejects a name that
  exactly matches another character (e.g. "Роналдо" for Ronaldinho); autocomplete with decoy names.
- Hint (category) for −200 points, skip / reveal, configurable wrong-answer penalty (0 / −100 / −200 / round points).
- Difficulty presets (easy / normal / hard), step duration 2 / 3 / 5 s, 5 / 10 / 15 rounds.
- ~55 characters (athletes, actors, musicians, scientists, film and cartoon characters) loaded from Wikimedia,
  with a Wikipedia REST API fallback and automatic replacement if an image fails to load.
- "Our team" round type: team members dressed as famous characters, mixed into every game (at least 3 per game,
  spread across rounds, never repeated in two consecutive games); the answer screen shows the original character
  fetched from Wikipedia. In this demo the team is six fictional people with generated SVG avatars (`team/`).
- Manual score editing (E), final results table with per-round tiles, keyboard shortcuts, fullscreen,
  sound effects synthesized with the Web Audio API (no audio files).
- Settings, recently shown characters and the team rotation queue are stored in `localStorage`.

## Tech stack

- One HTML file: HTML + CSS + vanilla JavaScript, no framework, no build step, no server
- Canvas 2D, CSS filters, Web Audio API, `localStorage`
- Images: Wikimedia Commons / Wikipedia REST API (loaded at runtime); fonts: Google Fonts

## Project structure

```
index.html     the whole game (styles, markup, character data, game logic)
team/          six fictional demo avatars (SVG) for the "Our team" rounds
```

## How to run

Open `index.html` in a browser (an internet connection is needed for the celebrity images and fonts),
or serve the folder:

```bash
python -m http.server 8000
# open http://localhost:8000
```

Keyboard: Space stop/continue · 1–6 team answers · H hint · S skip · N next round · E edit scores · F fullscreen · M sound.

To use your own team: put photos into `team/` and edit the `STAFF` array in `index.html`
(`staff('file.jpg', 'Name kk', 'Name ru', 'Costume', 'Wikipedia_article', ['answers'])`).

All data in this repository is randomly generated; brand names are anonymized.
Team members in `team/` are fictional; celebrity images are not stored in the repo, they are loaded from Wikimedia.

## Қысқаша (KZ)

«Пиксель & Блюр» — команда ойындарына арналған браузерлік викторина: танымал адамның суреті бұлыңғыр әрі
пиксельді болып басталып, бірте-бірте анықталады, ерте тапқан команда көбірек ұпай алады.
Бір ғана `index.html` файлы: HTML, CSS және JavaScript, Canvas пен Web Audio API.
Интерфейс қазақ және орыс тілінде. Іске қосу: `index.html` файлын браузерде ашыңыз.
«Біздің ұжым» бөліміндегі адамдар ойдан алынған.
