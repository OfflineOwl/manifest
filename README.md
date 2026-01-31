# OfflineOwl Official Registry

The official content registry for [OfflineOwl](https://offlineowl.app) - your offline survival and preparedness companion.

**This repository contains only metadata** (JSON index files). Actual content is hosted externally or in the [OfflineOwl Content](https://github.com/offlineowl/content) repository.

## Structure

```
registry/
├── registry.json              # Registry metadata
├── water-purification-guide.json
├── fire-starting-techniques.json
├── first-aid-fundamentals.json
├── ham-radio-basics.json
├── ...                        # All content JSON files at root
├── index.json                 # Auto-generated index
├── README.md
└── CONTRIBUTING.md
```

**Why flat?** Content often spans multiple categories. A shelter guide might also be a reference document. Instead of forcing a single folder, categorization happens in the JSON via `category`, `categories`, and `tags` fields.

## How It Works

Each JSON file in `content/` describes a piece of content and where to find it:

### External Content
Points to content hosted on CDNs, Archive.org, etc.

```json
{
  "id": "ham-radio-basics",
  "download": {
    "url": "https://cdn.offlineowl.app/content/ham-radio.pdf",
    "size": 12000000,
    "format": "pdf"
  }
}
```

### First-Party Content
Points to content in the [offlineowl/content](https://github.com/offlineowl/content) repo.

```json
{
  "id": "water-purification-guide",
  "localContent": {
    "repo": "https://github.com/offlineowl/content",
    "path": "guides/survival/water-purification",
    "format": "mdx"
  }
}
```

## Adding Content

See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

**To add external content:** Submit a PR to this repo with a JSON metadata file.

**To add first-party content:** Submit PRs to both this repo (metadata) and [offlineowl/content](https://github.com/offlineowl/content) (actual content).

## Using This Registry

Add this registry to your OfflineOwl app:

```
https://github.com/offlineowl/registry
```

## Categories

| Category | Description |
|----------|-------------|
| `survival` | General survival skills, water, fire |
| `medical` | First aid, health, medicine |
| `food-water` | Food preservation, water sourcing |
| `shelter` | Building shelter, staying warm |
| `communication` | Radio, signals, emergency communication |
| `entertainment` | Games, books, activities |
| `education` | Learning materials, courses |
| `reference` | Encyclopedias, manuals, databases |

## Related Repositories

- [offlineowl/offlineowl](https://github.com/offlineowl/offlineowl) - Main app (web, desktop, mobile)
- [offlineowl/content](https://github.com/offlineowl/content) - First-party authored content

## License

Metadata in this registry is public domain. Content items are licensed individually - see each item's `license` field.
