# 敬語道場 — Keigo Dojo

> A browser-based Japanese honorific practice game. No frameworks, no build step — just one HTML file.

---

## Overview

Keigo Dojo is a single-file HTML5 game for practising **keigo** (敬語), the formal register of Japanese. Each round presents a plain-form verb and asks you to produce the correct honorific form — either **sonkeigo** (尊敬語, elevating the other person) or **kenjōgo** (謙譲語, humbling yourself).

The game ends when you exhaust all 5 lives. Your score is tracked across the session with a streak multiplier for consecutive correct answers.

---

## Hosting on GitHub Pages

1. Create a new GitHub repository (e.g. `keigo-dojo`).
2. Place `index.html` in the repository root.
3. Go to **Settings → Pages**.
4. Under *Branch*, select `main` and folder `/root`, then click **Save**.
5. Your game will be live at:

```
https://<your-username>.github.io/keigo-dojo/
```

No build tools, package managers, or server required. GitHub Pages serves the file as-is.

---

## Game Modes

Toggle between modes using the pill selector at the top of the screen.

### Mode 1 — Multiple Choice

Three answer buttons appear per question:

| Option | Description |
|--------|-------------|
| Correct answer | The target honorific form (sonkeigo or kenjōgo) |
| Cross-category decoy | The other form of the same verb |
| Random decoy | An unrelated honorific expression from the pool |

**Keyboard shortcuts:**

| Key | Action |
|-----|--------|
| `A` / `1` | Select option A |
| `B` / `2` | Select option B |
| `C` / `3` | Select option C |
| `Enter` | Advance to next question (after answering) |

### Mode 2 — Type Answer

An input field accepts typed Japanese. Use your OS IME (Input Method Editor) to enter kana or kanji.

- A first-character hint is shown below the input field.
- Press `Enter` or click **確認 — Check** to submit.
- After answering, press `Enter` again to advance.

---

## Visual Feedback

| State | Background | Meaning |
|-------|------------|---------|
| 尊敬語 question | Blue gradient | Elevating the other person's action |
| 謙譲語 question | Green gradient | Humbling your own action |
| Wrong answer | Red flash | Incorrect — one life deducted |

The top border of the card and the background shift colour with each question type so you always have an ambient reminder of which register you are practising.

---

## Scoring

| Event | Points |
|-------|--------|
| Correct answer | +10 |
| Correct answer (3+ streak) | +20 (2× multiplier) |
| Wrong answer | 0 (−1 life) |

A streak counter is shown in the stats bar. It resets on any wrong answer.

---

## Lives

You start with **5 lives** (♥♥♥♥♥). Each wrong answer removes one heart. The game ends immediately when all five are lost. Your final score is shown on the game-over screen.

---

## Verb List

The game includes 20 verb pairs covering the most common irregular keigo forms.

| Base form | Reading | Meaning | 尊敬語 (Sonkeigo) | 謙譲語 (Kenjōgo) |
|-----------|---------|---------|-----------------|-----------------|
| する | suru | to do | なさる | いたす |
| いる | iru | to be | いらっしゃる | おる |
| 行く | iku | to go | いらっしゃる | 参る |
| 来る | kuru | to come | いらっしゃる | 参る |
| 言う | iu | to say | おっしゃる | 申す |
| 食べる | taberu | to eat | 召し上がる | いただく |
| 飲む | nomu | to drink | 召し上がる | いただく |
| もらう | morau | to receive | お受け取りになる | いただく |
| あげる | ageru | to give | くださる | 差し上げる |
| くれる | kureru | to give (to me) | くださる | 差し上げる |
| 知っている | shitte iru | to know | ご存じ | 存じている |
| 見る | miru | to see | ご覧になる | 拝見する |
| 聞く | kiku | to ask/listen | お聞きになる | 伺う |
| 思う | omou | to think | お思いになる | 存じる |
| 読む | yomu | to read | お読みになる | 拝読する |
| 書く | kaku | to write | お書きになる | 書かせていただく |
| 会う | au | to meet | お会いになる | お目にかかる |
| 待つ | matsu | to wait | お待ちになる | お待ちする |
| 使う | tsukau | to use | お使いになる | 使わせていただく |
| (visiting) | — | visiting | お越しになる | 伺う |

Each session rotates through verbs without immediate repeats. Once all 20 have appeared, the pool resets and reshuffles.

---

## Project Structure

```
keigo-dojo/
└── index.html    ← entire game (HTML + CSS + JS, self-contained)
```

Everything — markup, styles, game logic, and verb data — lives in a single file. There are no external dependencies beyond Google Fonts (loaded via CDN), so the game works fully offline if you remove the font import or cache it locally.

---

## Customisation

All verb data is stored in the `VERBS` array near the top of the `<script>` block in `index.html`. Each entry follows this shape:

```js
{
  base: "する",           // plain form shown to the player
  reading: "suru",       // romaji reading shown below
  meaning: "to do",      // English gloss shown in italics
  sonkeigo: "なさる",    // correct sonkeigo answer
  kenjougo: "いたす",    // correct kenjōgo answer
  decoys: [              // extra wrong answers specific to this verb
    "ございます", "おっしゃる", ...
  ]
}
```

To add more verbs, append objects in the same format to the `VERBS` array.

To change the number of lives, find `lives: 5` in the `state` object and update it.

---

## Browser Compatibility

Works in all modern browsers (Chrome, Firefox, Safari, Edge). Japanese IME input is handled natively by the OS — no special configuration needed.

---

## Licence

Free to use and modify for personal study.
