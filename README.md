# MDI Radar

A standalone Java 17 demonstration of extending the
[MDI scientific visualization framework](https://github.com/heddle/mdi) with
application-specific map projections, controls, items, and analysis.

MDI Radar combines country and city rendering, graticules, ETOPO5 terrain and
bathymetry, NATO military symbols, illustrative radar presets, and
terrain-aware line-of-sight visualization in an interactive MDI map view.

## Requirements

- Java 17 or newer
- Maven
- A graphical desktop environment

MDI 1.2.3 and the other dependencies are obtained automatically from Maven
Central. A separate local installation of MDI is not required.

## Build and run

From the root of the repository, build and test the application with:

```text
mvn clean verify
```

Run it with:

```text
mvn exec:java \
  -Dexec.mainClass=edu.cnu.mdi.radar.app.RadarApp
```

## Using the demonstration

- Select THAAD, Patriot, S1850M, or SPY-6 from the Radar Presets palette, then
  click the map to place it. Ground-based systems must be placed on land and
  ship-based systems on water.
- Drag a placed radar to move it and drag its azimuth handle to rotate its
  coverage sector.
- Colored radial segments show the lowest displayed target-altitude band with
  line of sight at each sampled range. Use the Target Altitudes slider to
  rescale those bands; the legend reports the current thresholds.
- Use the map controls to change projection or theme and to show or hide city
  names, graticules, labels, ETOPO5 shading, and hover feedback.
- The view popup provides quick zooms for the globe, Korean Theater, and
  USCENTCOM area of responsibility.
- Shapefiles can be opened from the Shapefiles menu or dropped onto the map and
  are rendered as ordinary MDI layers.
- Hover over a radar for its parameters, location, and boresight azimuth, or
  over the map for the underlying country and shapefile feedback.

The built-in radar parameters are illustrative values collected from open,
unclassified secondary sources. Published estimates vary, actual performance
may be classified, and the presets should be treated as visualization examples
rather than authoritative system specifications.

## Line-of-sight model

Line of sight is sampled outward from the radar across the terrain grid. The
calculation accounts for antenna height, terrain obstruction, the radar's
minimum elevation, and a four-thirds-Earth curvature correction. Negative
ETOPO5 elevations represent ocean depth and are treated as sea level—not as a
negative obstruction—for ship-based coverage.

Projection seams are detected so a coverage ray is not incorrectly drawn
across the map. The application-supplied Plate Carrée projection demonstrates
MDI's custom `IMapProjection` extension point.

## Architecture

- `RadarView` extends MDI's `MapView2D` and adds the radar palettes, target-
  altitude controls, quick zooms, and hover behavior.
- `RadarItem` implements projection-aware coverage drawing and terrain/curvature
  line-of-sight calculations on its own MDI layer.
- `RadarParameters` defines the four illustrative presets and their basing,
  antenna height, range, azimuth width, and minimum elevation.
- `PlateCarreeProjection` supplies an application-defined map projection.
- `Geodesy` contains the spherical-Earth destination, distance, and elevation-
  angle calculations used by the display.

Run the automated tests with:

```text
mvn test
```
