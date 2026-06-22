# Glimmer UI Spec & Glimmer Reader Details

## Overall Design Language
Calm, generous whitespace, excellent readable typography (system + optional elegant web font). Varied card layouts so the feed feels alive and human. Soft colors, high contrast for accessibility. 'Brutally elegant' reduction where possible — no unnecessary UI chrome.

## Feed
- Vertical scroll, responsive (mobile-first, beautiful on desktop too).
- Mixed or filtered by vibe/type.
- Each card distinct:
  - Animal/Cosmic: Image-forward, beautiful visuals.
  - Joke/Quote/Advice: Elegant text blocks with accent.
  - Literature: Typography preview card with author, short excerpt, 'Read in Glimmer Reader' prominent button.
- Load More button per section or global, with gentle 'Take a breath' prompt after batches.

## Glimmer Reader Modal (Core Differentiator)
Opened from Literature (or any text-heavy) cards.
- Full-bleed or contained calm modal.
- Top bar: Work title, author, close, share.
- Reading area: Customizable typography (controls in a gentle floating or top bar: font family toggle serif/sans, size slider or buttons, line height, max width, theme: light/sepia/dark).
- Content: Clean, justified or left-aligned text from excerpt or full PD work.
- Progress: Subtle bar or 'X of Y paragraphs' for longer pieces.
- Bottom actions: Favorite, 'Full text on Gutenberg / Standard Ebooks', 'Next delight'.
- Keyboard: Esc close, arrow keys if paginated, space for gentle scroll.
- Accessibility: ARIA, focus trap, high contrast options.

Implementation: React modal + content div with dynamic style from ReaderConfig (localStorage persisted). For full EPUB support in later phase or selected titles: Integrate futurepress/epub.js (permissive license) — load EPUB from URL or blob, render in container with its API for pagination, search, etc. Include example in prompts.

## Card Examples (Text Descriptions for Builder)
- Literature Card: Elegant serif preview, author italic, era tag, beautiful 'Open Reader' button with book icon.
- Cosmic Card: Large NASA image background or contained, overlay title + short explanation, 'Wonder more'.
- etc.

Make every interaction feel deliberate and delightful.