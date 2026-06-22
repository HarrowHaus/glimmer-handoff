# Glimmer API Catalog & Integration Notes

## Core Delight Sources (Fun, Wholesome, Visual, Contextual)

### 1. JokeAPI (https://sv443.net/jokeapi/v2/)
- Free, no key for most.
- Categories: Programming, Misc, Dark (filter safe), Single/Double.
- Integration: Fetch random or by category. Normalize to {type: 'joke', content: setup + delivery or single}.
- Notes: Excellent variety, reliable.

### 2. Quotable (https://quotable.io/)
- Clean random quotes, filters by tags/author.
- Great for elegant quote cards.

### 3. Dog CEO API (https://dog.ceo/api/breeds/image/random) + TheCatAPI
- Instant cute animal images. High delight density. Pair with cat facts for hybrid cards.

### 4. NASA APOD (https://api.nasa.gov/planetary/apod)
- Free key (quick signup at api.nasa.gov).
- Astronomy Picture of the Day + explanation. Perfect 'Cosmic Wonder' full-bleed or featured card. Use date param for variety or today.
- Proxy via server to hide key.

### 5. Open-Meteo (https://api.open-meteo.com/v1/forecast)
- Completely free, no key. Current + forecast weather.
- Use for contextual 'Weather Whimsy' card or theming (rainy = cozy content suggestions).
- Location via ipapi.co or browser geolocation (opt-in).

### 6. BoredAPI (https://www.boredapi.com/api/activity)
- Random activity suggestion. Spin positively as 'Wholesome Spark' or '5-min delight idea'.

### 7. Advice Slip API (https://api.adviceslip.com/advice)
- Free random micro-advice. Thoughtful short cards.

## Public Domain Literature, Poetry, Text & Books (The Deep Content Layer)

This is what makes Glimmer uniquely jam-packed and culturally rich.

### Project Gutenberg (https://www.gutenberg.org/)
- 75,000+ public domain ebooks (US).
- Texts available as plain text, HTML, EPUB.
- How to integrate for excerpts/random:
  - Use community wrappers or direct: e.g., https://www.gutenberg.org/files/{id}/{id}-0.txt for plain text.
  - For random: Maintain a small curated list of high-quality short works/poems/stories (IDs) or implement simple random ID + fetch + parse first paragraphs.
  - Categories: Literature, Poetry, Short Stories, Drama, History, Philosophy, Science.
  - Example flow: 'Literature & Letters' card type pulls random short excerpt (title, author, ~300 chars preview) from a themed or random Gutenberg text. 'Read in Glimmer Reader' opens modal.
- Full works: Link to gutenberg.org or host a few EPUBs.
- Public domain status: Confirmed US PD. Perfect for ethical, sovereign content.

### Standard Ebooks (https://standardebooks.org/)
- High-quality, professionally formatted public domain EPUBs (carefully typeset, proofread).
- Direct EPUB download links.
- Ideal for **EPUB.js** integration in Glimmer Reader modal for immersive, beautiful reading of short stories, novellas, poetry collections.
- Integration: Curate 10-20 favorites or dynamic via their OPDS/feed if available. Proxy or CORS-friendly hosting for selected titles.

### Open Library / Internet Archive (https://openlibrary.org/)
- API for search, works, editions, covers, some full texts.
- Great for metadata + covers for literature cards or 'Book Glimmers'.

### Wikisource & Other PD Sources
- Public domain texts with good formatting.
- Wikipedia API for 'On This Day in Literature/History' or short excerpts (with attribution).
- HathiTrust for additional PD volumes.

### Integration Strategy for Literature
- **Feed Card**: Short preview + metadata (author, era, tags like 'Poetry 19thC', 'Short Story').
- **Glimmer Reader Modal**: Calm reading experience with:
  - Typography controls (serif/sans, size 16-24px, line-height, max-width).
  - Progress indicator for longer excerpts.
  - 'Full text on Gutenberg' or 'Open in Standard Ebooks' external link.
  - Optional: Wire futurepress/epub.js for full EPUB rendering of selected high-quality editions (include via <script> or npm in Next.js, example usage in prompts).
- Caching: Server or edge cache excerpts and popular texts. Fetch full on reader open.
- Performance: Always short previews in feed; deeper read on demand.

## Additional / Future Sources
- xkcd JSON for nerdy fun comic cards.
- Art Institute of Chicago API for public domain art 'Visual Delight' cards.
- Numbers API or historical trivia for 'Mind Spark' facts.
- All sources proxied server-side (Next.js Route Handlers) for CORS, key hiding, rate limit smoothing, and simple caching.

Rate limits & Reliability: Most are generous for personal/MVP use. Monitor and add fallbacks/graceful degradation. All chosen for being actively maintained or stable public resources as of 2026.

Proxy everything in /api/glimmer/[source] routes for clean client calls.