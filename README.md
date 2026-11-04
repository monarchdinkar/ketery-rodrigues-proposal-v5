# Kétery's Little Universe · V6

A cinematic, music-synchronised proposal site, built around an original song
(words and voice by Monarch). The site is a static page with no build step and runs on GitHub Pages.

## Files
| File | Purpose |
| --- | --- |
| `index.html` | The whole site: HTML, CSS, JS, inline SVG art, lyric timings |
| `Proposal.mp3` | The song (drives the entire timeline) |
| `og.png` | 1200×630 link-preview image (WhatsApp / iMessage) |
| `icon.svg`, `favicon-32.png`, `apple-touch-icon.png` | Icons |

## Deploy (GitHub Pages)
1. Merge this branch into `main`.
2. **Settings → Pages → Deploy from a branch → `main` → `/ (root)`**.
3. The site appears at `https://monarchdinkar.github.io/ketery-rodrigues-proposal-v5/`.
   The `og:image` / `og:url` tags already point there. If the repo name changes, update them in `index.html`.
4. Before sending, paste the link into a WhatsApp chat with yourself to check the preview.
   WhatsApp caches previews, so if it shows the old one, add `?v=2` to the link.

## How the story is timed
Everything follows `audio.currentTime` in one `requestAnimationFrame` loop:

| Time (s) | Section | Scene |
| --- | --- | --- |
| 0–14 | Intro | Two worlds: Agra, India ↔ São Paulo, Brazil |
| 14–26.6 | Verse | Witchy universe (caos, tarot, crystals) |
| 26.6–40 | Verse | Pastel dreamland (side quests) |
| 40–47 | Pre-chorus | Magical library |
| 47–72.8 | Chorus | Enchanted forest (lyrics lead) |
| 72.8–94.2 | Bridge | Rain, then waterfall and rainbow |
| 94.2–126 | Final + outro | Dawn. The question card appears at **101.1 s** |
| after YES | — | Celebration, song reveal, love letter |

Lyric word timings were aligned to the MP3 with Whisper (word timestamps), then mapped
onto the exact lyrics.

## Fine-tuning the lyric timing
1. Open the site with `?debug=1` (e.g. `index.html?debug=1`).
2. Use **▶ from line** / **⏯** to listen. **◀ line / line ▶** (or ↑/↓) select a line, and
   **−0.1s / +0.1s** (or ←/→) shift the whole line. Click the progress bar to seek.
3. Press **Export**. The full `const LYRICS=[…]` block is copied to your clipboard.
4. In `index.html`, replace the existing `const LYRICS=[ … ];` block with it.

Other timing constants live right below it: `SECTIONS`, `QUESTION_T`, `RAIN_STOP`, `RAINBOW_T`.

## Controls
- Space play/pause · M mute · R restart · ←/→ previous/next chapter (while paused).
- Swipe changes chapters while paused.
- If the MP3 can't load, the site switches to a read-through mode with ‹ › buttons.

## Characters & their moments
Monarch and Kétery appear as soft, backlit silhouettes, built in SVG inside `index.html` (`buildCast`):

| Chapter | Moment |
| --- | --- |
| Two worlds | Monarch waves from Agra, Kétery waves back from São Paulo. A heart travels between them |
| Your magic | Kétery as a little witch, with a hat and a wand that throws sparkles |
| Side quests | Monarch the fixer with his wrench, while Kétery laughs (“haha”) |
| Library | Both reading by candlelight, pages flipping |
| Chorus | Holding hands under the tree, the two dogs and two cats around them (tails wagging) |
| Bridge | Monarch holds an umbrella over her in the rain. When the rainbow appears, it closes and she points at it |
| Dawn | Monarch offers a glowing heart |
| YES | Both jump for joy with the pets, hearts rising |

Extra motion: shooting stars, butterflies, birds at dawn, rain splashes, and a slow camera drift.

## Performance on different phones
- Older or low-memory Android phones start in **lite mode**. It uses fewer particles, a lower canvas resolution, and no blur or glow filters.
- Every device measures its own frame rate while the song plays and steps quality down automatically if it drops.
- Layouts are tested at 320×568, 360×640, 375×667, 360×780, 390×844, 412×915, 430×932, iPad portrait and landscape, 740×360 landscape, and desktop.
- On portrait phones, the side-quest and postcard cards take turns instead of crowding the screen.

## Hidden easter eggs
Tap a tarot card · tap “caos” · tap the sleeping pets · tap “Amata Lux” (or type `amatalux`).
