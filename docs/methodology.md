# Methodology

## Data Sources

- **OCHA COD-AB Mali v03** (CC BY-IGO) — 20 regions + 160 cercles with P-codes (2025 restructure)
- **Mali agricultural census form (fiche_attach.xlsx)** — Full 4-level hierarchy with hierarchical codes: 19 regions, 159 cercles, 474 arrondissements, 816 communes
- **GeoNames** (CC BY 4.0) — Coordinates for cercles, arrondissements, communes
- **OpenStreetMap Nominatim** — Fallback geocoding
- **CITADEL-BF/WeatherDemo** — Supplementary coordinates

## Processing

1. Region and cercle layer from OCHA COD-AB (authoritative P-codes + coords)
2. Arrondissement and commune layers from agricultural census form (hierarchical codes)
3. Parent-child relationships linked via code prefix matching
4. Coordinates from GeoNames + Nominatim + parent-centroid fallback
5. Multi-format export: JSON, NDJSON, CSV

## Important Notes

- Mali restructured from 8 to 20 regions in 2025 — this dataset uses the new structure
- Mali does not have an area-based postal code system
- Arrondissements are territorial divisions without administrative power; communes are local government units
- This is believed to be the only open dataset with all 4 levels of Mali's administrative hierarchy

## Accuracy

- Coordinates: 100% at all levels (mix of precise + parent-centroid fallback)
- Names: 100% at all levels (French)
- Build script is idempotent: same input always produces same output