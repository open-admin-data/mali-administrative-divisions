# Mali Administrative Divisions / Mali

Open dataset of Mali's complete administrative hierarchy — 20 regions, 160 cercles, 474 arrondissements, and 816 communes. This is the only known open dataset with all four levels of Mali's 2025 administrative structure. French language reference data with geographic coordinates at every level. Designed for developers, researchers, government agencies, and AI agents.

Licensed under CC-BY-4.0. Browse the hierarchy through GitHub's folder navigation, download aggregate files in JSON/CSV/NDJSON, or integrate directly via raw URLs.

## Overview

| Item | Details |
|------|---------|
| Region | 20 |
| Circle | 160 |
| Arrondissement | 474 |
| Commune | 816 |
| Coordinates | ✅ Included (all levels) |
| Formats | JSON, NDJSON, CSV |
| License | CC-BY-4.0 |
| Last Updated | 2026-06-01 |
| Website | [openadmindata.org/ml](https://openadmindata.org/ml/) |
| API | [openadmindata.org/api/ml](https://openadmindata.org/api/ml/) |

## Browse by Region

| # | Region | Circles | Arrondissements | Communes | Link |
|---|----|----|----|----|------|
| 1 | Kayes | 10 | 33 | 65 | [Browse](divisions/kayes-ml01/) |
| 2 | Koulikoro | 8 | 26 | 58 | [Browse](divisions/koulikoro-ml02/) |
| 3 | Sikasso | 8 | 13 | 36 | [Browse](divisions/sikasso-ml03/) |
| 4 | Segou | 11 | 28 | 54 | [Browse](divisions/segou-ml04/) |
| 5 | Mopti | 8 | 34 | 50 | [Browse](divisions/mopti-ml05/) |
| 6 | Tombouctou (Timbuktu) | 13 | 30 | 47 | [Browse](divisions/timbuktu-ml06/) |
| 7 | Gao | 16 | 37 | 40 | [Browse](divisions/gao-ml07/) |
| 8 | Kidal | 9 | 29 | 30 | [Browse](divisions/kidal-ml08/) |
| 9 | Taoudenni | 6 | 30 | 30 | [Browse](divisions/taoudenni-ml09/) |
| 10 | Ménaka | 6 | 18 | 27 | [Browse](divisions/mnaka-ml10/) |
| 11 | Nioro | 6 | 4 | 10 | [Browse](divisions/nioro-ml11/) |
| 12 | Kita | 6 | 14 | 33 | [Browse](divisions/kita-ml12/) |
| 13 | Dioïla | 6 | 13 | 23 | [Browse](divisions/diola-ml13/) |
| 14 | Nara | 6 | 12 | 14 | [Browse](divisions/nara-ml14/) |
| 15 | Bougouni | 10 | 22 | 41 | [Browse](divisions/bougouni-ml15/) |
| 16 | Koutiala | 8 | 22 | 46 | [Browse](divisions/koutiala-ml16/) |
| 17 | San | 7 | 17 | 42 | [Browse](divisions/san-ml17/) |
| 18 | Douentza | 6 | 15 | 21 | [Browse](divisions/douentza-ml18/) |
| 19 | Bandiagara | 9 | 28 | 48 | [Browse](divisions/bandiagara-ml19/) |
| 20 | Bamako | 1 | 0 | 0 | [Browse](divisions/bamako-ml20/) |

## Data Files

| File | Format | Description |
|------|--------|-------------|
| [all-region.json](data/all-region.json) | JSON | All 20 region records |
| [all-cercle.json](data/all-cercle.json) | JSON | All 160 circle records |
| [all-arrondissement.json](data/all-arrondissement.json) | JSON | All 474 arrondissement records |
| [all-commune.json](data/all-commune.json) | JSON | All 816 commune records |
| [all-flat.json](data/all-flat.json) | JSON | Levels 1-3 flat array |
| [all-flat.ndjson](data/all-flat.ndjson) | NDJSON | Streaming format |
| [all-flat.csv](data/all-flat.csv) | CSV | Spreadsheet format |
| [hierarchy.json](data/hierarchy.json) | JSON | Nested tree |
| [schema.json](data/schema.json) | JSON Schema | Data schema |

## Quick Start

### Python

```python
import json

with open("data/all-region.json", "r", encoding="utf-8") as f:
    data = json.load(f)

for r in data:
    print(f"{r['name']['local']} ({r['name']['en']}) — {r['children_count']['cercle']} circles")
```

### JavaScript

```javascript
import { readFileSync } from "fs";

const data = JSON.parse(readFileSync("data/all-region.json", "utf-8"));
console.log(`Total: ${data.length} regions`);
```

## Schema

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier |
| `level` | integer | 1=region, 2=circle, 3=arrondissement, 4=commune |
| `level_name` | object | Level label (local + English) |
| `name.local` | string | Name in local script |
| `name.en` | string | English name |
| `name.slug` | string | URL-safe slug |
| `parent` | object/null | Parent division reference |
| `ancestors` | array | Full ancestor chain |
| `children_count` | object | Count of children per level |
| `zip_codes` | array | Postal codes (where available) |
| `geo.lat` | string | Latitude (WGS84) |
| `geo.lon` | string | Longitude (WGS84) |

Full schema: [data/schema.json](data/schema.json)

## Hierarchy Browse

```
divisions/{region-slug}/
divisions/{region-slug}/{cercle-slug}/
divisions/{region-slug}/{cercle-slug}/{arrondissement-slug}/
```

Communes are listed inline in each arrondissement's README.

## AI Integration

- [llms.txt](docs/llms.txt) — Quick reference for AI agents
- [llms-full.txt](docs/llms-full.txt) — Summary with per-region links
- [Per-region data](docs/llms-full/) — Full data by region

## Citation

```
Mali Administrative Divisions Dataset (CC-BY-4.0)
URL: https://github.com/open-admin-data/mali-administrative-divisions
```

See [CITATION.cff](CITATION.cff) for machine-readable citation.

## License

- **Data**: [CC-BY-4.0](LICENSE)

## Related

- [Open Admin Data](https://openadmindata.org) — Browse, search and explore administrative divisions for every country
- [open-admin-data](https://github.com/open-admin-data) — GitHub organization with all country repos
- [ListBase](https://www.listbase.org) — Structured reference data for every country
