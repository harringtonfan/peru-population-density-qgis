# Peru Population Density Map in QGIS

This project is a first attempt at creating population density maps of Peru in QGIS using `GHSL GHS-POP 2025` population data, inspired by Mashford Mahute’s population density mapping workflow.

The goal was not only to reproduce a similar visual style, but also to better understand how far the same workflow can translate across different countries. One of the main takeaways from this project is that it does not translate automatically. Egypt’s population distribution creates a very strong visual structure for this type of map, while Peru’s population pattern is much more dispersed across the coast, the Andes, and the interior, which makes the cartographic challenge quite different.

![Peru population density map](new_peru.png)

## Project goals

- Build Peru population density maps in QGIS using `GHSL GHS-POP 2025`
- Experiment with raster styling, layout composition, and dark-background cartography
- Learn a QGIS workflow involving `VRT` construction, clipping, `Singleband pseudocolor` symbology, and print layout design
- Test whether adding terrain structure could improve the final visual result

## Data sources

- **`GHSL GHS-POP 2025`**  
  Global Human Settlement Layer population raster used as the main population density data source.

- **`Natural Earth`**  
  Used for Peru national boundary extraction and masking.

- **`NASADEM` (attempted)**  
  I also experimented with terrain integration using `NASADEM` in order to add more relief and structure to the map, but did not complete that part in the final version because it became more technically involved than expected.

## Workflow

### 1. Download population data
Downloaded `GHSL GHS-POP 2025` tiles covering Peru.

### 2. Build a virtual raster
Merged the tiles into a single `VRT` in QGIS.

### 3. Clip to Peru boundary
Extracted Peru from `Natural Earth` country boundaries and used it to clip the raster with `peru_boundary`.

### 4. Style the raster
Styled the clipped raster in QGIS using:

- `Singleband pseudocolor`
- `Linear` interpolation
- dark-background map composition
- multiple rounds of color ramp and value range adjustment

### 5. Layout design
Created print layouts with:

- black background
- minimal white national outline
- a simple title treatment

### 6. Terrain experiment
I attempted to incorporate `NASADEM`-derived terrain to make the map feel less flat, but the integration process became more complicated than expected, so I stopped at a simpler first iteration rather than forcing a partial result into the final map.

## Main challenges

This project involved much more trial and error than I initially expected. Some of the main issues included:

- incomplete `GHSL` tile coverage at first
- rebuilding `VRT`s after adding missing raster tiles
- extracting a clean Peru boundary for clipping
- repeated adjustments to `Singleband pseudocolor` symbology and cumulative count cut settings
- trying to make the map feel less flat without overcomplicating the workflow
- realizing that Peru does not naturally produce the same kind of dramatic visual structure as Egypt under the same mapping logic

## Reflection

This project was a useful reminder that a strong map is not only about technical workflow. It also depends on the spatial structure of the place itself.

Egypt’s population density pattern creates an unusually dramatic visual logic for this kind of dark-background heat map. Peru is different. Its population is distributed more unevenly across coast, mountains, and interior regions, so the same workflow produces a different visual result and likely requires a different final rendering strategy.

I also suspect that the final image would benefit from an additional terrain or relief layer, but that part remains unfinished in this version.

## Close-up detail

A closer look at part of the map, highlighting the finer settlement texture and density patterns that become more visible at a more local scale.

![Peru population density detail](peru_part1.png)

## Files

- `new_peru.png` — national-scale version
- `peru_part1.png` — close-up detail view

## Notes

This repository focuses on documenting the workflow and outputs rather than packaging all raw raster data, since the source files are large. Raw population and DEM data should be downloaded directly from the original sources listed above.