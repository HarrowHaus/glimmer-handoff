# Glimmer Data Models (TypeScript / Zod ready)

```ts
import { z } from 'zod';

export const DelightTypeSchema = z.enum([
  'joke', 'quote', 'animal', 'fact', 'cosmic', 'weather', 'activity', 'advice', 'literature', 'art'
]);

export const VibeTagSchema = z.enum([
  'cozy', 'curious', 'playful', 'whimsical', 'inspiring', 'literary', 'cosmic'
]);

export const DelightCardSchema = z.object({
  id: z.string(),
  type: DelightTypeSchema,
  title: z.string().optional(),
  content: z.string(), // preview or main text
  imageUrl: z.string().url().optional(),
  meta: z.record(z.any()).optional(), // source, author, era, weather info, etc.
  vibeTags: z.array(VibeTagSchema),
  sourceUrl: z.string().url().optional(), // Gutenberg, NASA, etc.
  epubUrl: z.string().url().optional(), // for EPUB.js
  timestamp: z.string(),
});

export type DelightCard = z.infer<typeof DelightCardSchema>;

// For Glimmer Reader

export const ReaderConfigSchema = z.object({
  fontFamily: z.enum(['serif', 'sans']).default('serif'),
  fontSize: z.number().min(14).max(28).default(18),
  lineHeight: z.number().min(1.4).max(2).default(1.7),
  maxWidth: z.number().min(600).max(900).default(720),
  theme: z.enum(['light', 'sepia', 'dark']).default('light'),
});

export type ReaderConfig = z.infer<typeof ReaderConfigSchema>;

// Literature specific extension example
export const LiteratureMetaSchema = z.object({
  author: z.string(),
  era: z.string().optional(),
  workTitle: z.string(),
  excerptLength: z.number(),
  fullTextAvailable: z.boolean(),
});
```

Use these for type safety across feed, cards, reader, and storage.