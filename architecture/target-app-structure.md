# Target App Architecture for Glimmer

## Recommended Stack
Next.js 15 App Router + TypeScript + Tailwind + shadcn/ui (or Radix). Server Components where possible. React Query or native fetch with caching for feed.

Why: AI agents love this stack. One-command Vercel deploy. Excellent for component-driven UI with varied cards. Easy proxy routes. PWA trivial.

Alternative: Heroic single-file (HTML + Tailwind CDN + TS) for ultra-rapid prototype of core feed + reader — then migrate.

## Folder Structure (Target Built App)
```
glimmer/
├── app/
│   ├── layout.tsx
│   ├── page.tsx                 # Landing + entry to feed
│   ├── feed/
│   │   └── page.tsx             # Main rich scrollable feed
│   └── api/glimmer/
│       ├── [source]/route.ts    # Proxy for each API source (joke, nasa, gutenberg-excerpt, etc.)
│       └── literature/[id]/route.ts
├── components/
│   ├── DelightCard/             # Polymorphic or type-specific cards
│   │   ├── JokeCard.tsx
│   │   ├── LiteratureCard.tsx   # Special with reader trigger
│   │   └── ...
│   ├── GlimmerReader.tsx        # The calm modal reader + controls
│   ├── Feed.tsx
│   └── ui/                      # shadcn components
├── lib/
│   ├── sources/                 # Modular fetchers + normalizers
│   │   ├── joke.ts
│   │   ├── literature-gutenberg.ts  # Excerpt logic, PD handling
│   │   ├── nasa.ts
│   │   └── index.ts
│   ├── types.ts                 # DelightCard, ReaderConfig, etc.
│   └── utils.ts
├── hooks/
│   └── useLocalStorage.ts       # Favorites, prefs, recent
└── public/                      # Manifest, icons for PWA
```

## Key Technical Decisions
- All external calls proxied in /api/glimmer/* for security, caching (simple in-memory or Vercel KV), rate smoothing.
- Literature: Short excerpts in feed; full or longer in reader. Use Gutenberg plain text or Standard Ebooks EPUB where wired.
- State: Minimal, localStorage primary for v0.1.
- Performance: Skeleton loaders beautiful, optimistic updates for favorites, image optimization.
- EPUB.js (optional/advanced): Install via npm, dynamic import in reader for selected titles. Example code in prompts.

## Mermaid Flow (Simplified Feed Load)
```mermaid
graph TD
    User[User opens feed] --> Fetch[Proxy fetch mixed sources]
    Fetch --> Normalize[Normalize to DelightCard[]]
    Normalize --> Render[Render varied cards]
    Render --> Interact[User filters / loads more / opens Reader]
    Interact --> Reader[Beautiful typography modal]
```

This structure is AI-buildable in focused phases and highly extensible (add new sources in lib/sources/ easily).