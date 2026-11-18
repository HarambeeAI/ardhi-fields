# ardhi-fields

Field-boundary map tiles read by the [ARDHI 1](https://ardhi-1--lawlyfyai.replit.app/) app.

The files are served by GitHub Pages at `https://harambeeai.github.io/ardhi-fields/`. The app reads `manifest.json` there, which lists each layer's tile file and the area it covers, and then fetches only the few tiles under the area being analysed.

## What is here

| File | Area | Fields |
|---|---|---|
| `musanze.pmtiles` | Musanze district, Rwanda | 37,663 |
| `mbale.pmtiles` | Mbale district, Uganda | 56,437 |
| `tamale.pmtiles` | Half-degree box around Tamale, Ghana | 555,192 |
| `chipata.pmtiles` | Chipata district, Zambia | 238,222 |
| `east_shewa.pmtiles` | East Shewa zone, Ethiopia | 1,528,997 |
| `kenya_1.pmtiles` to `kenya_4.pmtiles` | Western Kenya, west of about 36.4°E | 5,918,749 |
| `kenya_b_1.pmtiles` to `kenya_b_4.pmtiles` | Central Kenya (the central highlands, Nairobi and south to the border, about 36.3°E to 38.1°E) and the north-west, where there are few fields | 6,094,416 |
| `manifest.json` | The list of layers the app reads | |

Each file is a [PMTiles](https://docs.protomaps.com/pmtiles/) archive with one vector layer, `fields`, at zoom 14. Every field has `id`, `area_ha`, `confidence` (the model's mean probability inside the field, 0 to 1) and `source` (`ardhi` or `ftw`).

## How the fields were made

- **`source: ardhi`**: drawn by the Ardhi field-boundary model from Sentinel-2 mosaics of 2024 and 2025. The model finds most cropland, but it draws a real field as two to three outlines on average, and it outlines some grassland, fallow and settlement as fields. Treat counts and "share farmed" as upper bounds.
- **`source: ftw`**: where [Fields of The World](https://fieldsofthe.world) draws a compact field of 4 to 50 ha, that field is used in place of ours, because our model cuts large fields into pieces.

Built on 17 and 18 November 2026. Kenya is being built in parts: 39 of its 89 Sentinel-2 tiles are done, and each part is a separate layer cut into files under 100 MB. These are model outputs, not surveyed or legal parcels.

## Credits and terms

- Fields marked `ftw` come from Fields of The World (CC BY 4.0): credit "Fields of The World" when you use them.
- The Sentinel-2 mosaics the model read are Fields of The World's public composites of Copernicus Sentinel data.
- No licence has been chosen yet for the fields marked `ardhi`. Until one is added here, ask before reusing them.
