# Contributing to the OfflineOwl Manifest

Thank you for your interest in contributing to the OfflineOwl content manifest!

## Important: Two Repositories

| Repository | Purpose |
|------------|---------|
| **This repo** (`manifest`) | JSON metadata files only |
| [offlineowl/content](https://github.com/offlineowl/content) | First-party authored content (guides, games, etc.) |

**This repo is intentionally lightweight** - just JSON files that index content. This makes it easy for the community to browse, edit, and contribute without navigating through hundreds of content files.

## Manifest Structure

```
manifest/
├── registry.json              # Registry metadata
├── water-purification-guide.json
├── first-aid-fundamentals.json
├── ham-radio-basics.json
├── ...                        # All JSON files flat at root
├── index.json                 # Auto-generated index (do not edit manually)
└── CONTRIBUTING.md            # This file
```

**Flat structure** - No category folders. Categories are defined in the JSON itself, allowing content to belong to multiple categories.

---

## Naming Convention

**Filename**: `{slug}-{id}.json`
**ID in JSON**: Just the 4-char id

```
Filename: water-purification-a7x9.json
ID: "a7x9"
```

- **Slug**: Descriptive, lowercase, hyphens only (for human readability)
- **ID**: 4 random alphanumeric characters (the unique identifier)

### Generating an ID

Use the [ID Generator Tool](https://offlineowl.com/tools/id-generator) to:
1. Enter your content title
2. Get a unique 4-char ID
3. Check availability against existing manifest
4. Use ID for both filename suffix and JSON id field

---

## Adding External Content

For content already hosted elsewhere (Archive.org, CDN, etc.):

1. **Create a JSON file** at root: `{slug}.json`
2. **Include a `download` object** with the URL

### External Content Schema

```json
{
  "id": "a7x9",
  "version": "1.0.0",
  "title": "My Content Title",
  "description": "Full description of the content...",
  "shortDescription": "Brief summary (optional)",
  "type": "document",
  "category": "survival",
  "categories": ["survival", "reference"],
  "tags": ["water", "purification", "emergency"],
  "download": {
    "url": "https://example.com/file.pdf",
    "mirror": "https://archive.org/download/file.pdf",
    "size": 1234567,
    "checksum": {
      "algorithm": "sha256",
      "value": "abc123..."
    },
    "format": "pdf"
  },
  "license": "cc-by-sa",
  "author": "Author Name",
  "language": "en",
  "createdAt": "2026-01-30T00:00:00.000Z",
  "updatedAt": "2026-01-30T00:00:00.000Z",
  "verified": false,
  "featured": false,
  "priority": 50
}
```

**Note:** Use `category` for the primary category and `categories` array for additional cross-listing.

---

## Adding First-Party Content

For original content you're creating (guides, games, tools):

### Step 1: Create Content in the Content Repo

Submit a PR to [offlineowl/content](https://github.com/offlineowl/content):

```
content/
├── guides/{category}/{slug}/
│   ├── index.mdx
│   └── assets/
├── games/{slug}/
│   ├── index.html
│   ├── game.ts
│   └── assets/
└── tools/{slug}/
```

### Step 2: Create Metadata in This Repo

Submit a PR here with `{slug}-{code}.json` at the root (e.g., `my-guide-k2m3.json`):

```json
{
  "id": "k2m3",
  "version": "1.0.0",
  "title": "My Guide Title",
  "description": "Detailed description...",
  "type": "guide",
  "category": "survival",
  "categories": ["survival", "reference"],
  "tags": ["relevant", "tags"],
  "localContent": {
    "repo": "https://github.com/offlineowl/content",
    "path": "guides/survival/my-guide-k2m3",
    "ref": "main",
    "entryPoint": "index.mdx",
    "format": "mdx"
  },
  "license": "cc-by-sa",
  "author": "Your Name",
  "language": "en",
  "createdAt": "2026-01-31T00:00:00.000Z",
  "updatedAt": "2026-01-31T00:00:00.000Z",
  "verified": false,
  "featured": false,
  "priority": 50,
  "metadata": {
    "estimatedReadTime": "10 minutes"
  }
}
```

---

## Content Types

- `document` - PDF, EPUB, text files (external)
- `guide` - MDX/Markdown guides (first-party)
- `video` - MP4, WebM videos
- `audio` - MP3, OGG audio files
- `image` - PNG, JPG, WebP images
- `game` - Interactive games/activities (first-party)
- `tool` - Interactive tools/calculators (first-party)
- `ai-model` - LLM models for offline use
- `archive` - ZIP, compressed collections
- `dataset` - Structured data files

### Categories

- `survival` - General survival skills
- `medical` - First aid, health information
- `food-water` - Food preservation, water purification
- `shelter` - Building and maintaining shelter
- `communication` - Radio, signals, staying connected
- `entertainment` - Games, media, activities
- `education` - Learning resources
- `reference` - Manuals, guides, encyclopedias

### Licenses

Use one of these license identifiers:
- `public-domain` - No copyright restrictions
- `cc0` - Creative Commons Zero
- `cc-by` - Creative Commons Attribution
- `cc-by-sa` - CC Attribution ShareAlike
- `cc-by-nc` - CC Attribution NonCommercial
- `cc-by-nc-sa` - CC Attribution NonCommercial ShareAlike
- `mit` - MIT License
- `apache-2.0` - Apache License 2.0
- `gpl-3.0` - GNU GPL v3
- `proprietary` - Proprietary (with permission)
- `custom` - Custom license (include licenseUrl)

## Requirements for Contributions

1. **Content must be legally distributable** - You must have rights to share the content
2. **Provide accurate checksums** - Use SHA256 for file verification
3. **Host content reliably** - URLs should be stable and accessible
4. **Include mirrors when possible** - Backup URLs improve availability
5. **Use appropriate licenses** - Clearly specify the license

## Generating the Index

After adding or modifying content, regenerate the index:

```bash
npx @offlineowl/manifest build-index .
```

This will update `index.json` with the latest content metadata.

## Creating Your Own Manifest

You can create your own manifest by:

1. Fork this repository structure
2. Modify `registry.json` with your manifest's metadata
3. Add your content items
4. Host your repository (GitHub, GitLab, etc.)
5. Users can add your manifest URL in OfflineOwl

### Registry Types

- `official` - Maintained by OfflineOwl team
- `verified` - Community registry that's been reviewed
- `community` - Public community registry
- `personal` - Private/personal registry

## Questions?

Open an issue or discussion if you have questions about contributing!
