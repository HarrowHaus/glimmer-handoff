Phase 2: Rich Feed + Literature Source + Glimmer Reader Modal.

Build on Phase 1.

Implement the main /feed page with:
- Mixed feed loading from multiple proxied sources (include at least Joke/Quote/Animal + one Literature source from Gutenberg or curated PD excerpt).
- Vibe filters and Surprise Me that mixes card types.
- LiteratureCard component that shows elegant preview + 'Read in Glimmer Reader'.
- Full GlimmerReader modal wired to literature (and extensible to other text cards). Include typography controls persisting to localStorage, progress, calm design.
- Basic favorites + recent history using localStorage.
- Load more functionality (user-controlled).

For Literature integration: Implement a simple gutenberg-excerpt fetcher (use a few reliable PD IDs or random logic + parse first paragraphs for preview). Or start with static curated high-quality short excerpts and wire dynamic later.

Wire basic custom reader first (div + style controls). Add note/comment for future EPUB.js integration (example: dynamic import of epubjs and render in container).

Test: Open feed, filter to Literary, open a card in reader, change typography, favorite, share.

Output full code for new files and diffs. Confirm end-to-end working with real PD content.