# Contributing to the OfflineOwl Registry

Thank you for your interest in contributing to the OfflineOwl content registry!

## Registry Structure

```
registry/
├── registry.json          # Registry metadata
├── content/               # Content items organized by category
│   ├── survival/
│   ├── medical/
│   ├── food-water/
│   ├── shelter/
│   ├── communication/
│   ├── entertainment/
│   ├── education/
│   └── reference/
├── index.json             # Auto-generated index (do not edit manually)
└── CONTRIBUTING.md        # This file
```

## Adding New Content

1. **Choose the correct category** for your content
2. **Create a new JSON file** in the appropriate category folder
3. **Name the file** using the content ID (lowercase, hyphenated): `my-content-item.json`
4. **Follow the schema** defined below

### Content Item Schema

```json
{
  "id": "my-content-item",
  "version": "1.0.0",
  "title": "My Content Title",
  "description": "Full description of the content...",
  "shortDescription": "Brief summary (optional)",
  "type": "document",
  "category": "survival",
  "tags": ["tag1", "tag2"],
  "download": {
    "url": "https://example.com/file.pdf",
    "mirror": "https://backup.example.com/file.pdf",
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

### Content Types

- `document` - PDF, EPUB, text files
- `video` - MP4, WebM videos
- `audio` - MP3, OGG audio files
- `image` - PNG, JPG, WebP images
- `game` - Interactive games/activities
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
npx @offlineowl/registry build-index .
```

This will update `index.json` with the latest content metadata.

## Creating Your Own Registry

You can create your own registry by:

1. Fork this repository structure
2. Modify `registry.json` with your registry's metadata
3. Add your content items
4. Host your repository (GitHub, GitLab, etc.)
5. Users can add your registry URL in OfflineOwl

### Registry Types

- `official` - Maintained by OfflineOwl team
- `verified` - Community registry that's been reviewed
- `community` - Public community registry
- `personal` - Private/personal registry

## Questions?

Open an issue or discussion if you have questions about contributing!
