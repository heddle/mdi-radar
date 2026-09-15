# Changelog

All notable changes to the MDI Radar demonstration are documented in this
file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/).

No changelog was kept during initial development, so the 1.0.0 entry has been
reconstructed from the project history.

## [Unreleased]

## [1.0.0] - 2026-09-15

### Added

- Standalone MDI map application with country and city data, graticules,
  ETOPO5 terrain and bathymetry, themes, projections, and shapefile layers.
- Illustrative THAAD, Patriot, S1850M, and SPY-6 radar presets with land/ship
  placement rules, draggable sites, and adjustable boresight azimuth.
- Terrain-aware radar line-of-sight visualization accounting for antenna
  height, terrain masking, minimum elevation angle, and four-thirds-Earth
  curvature.
- Colored range segments and a scalable legend showing the target altitude
  required for line of sight.
- NATO military-symbol palette and application-specific radar item layer.
- Application-supplied Plate Carrée projection demonstrating MDI's custom
  projection API, including inverse transforms and seam handling.
- Global, Korean Theater, and USCENTCOM quick-zoom commands.
- Optional hover feedback for radar parameters, site coordinates, boresight,
  countries, and shapefile attributes.
- `RadarViewInfo` documentation integrated with the MDI view-information
  mechanism.

### Changed

- Refactored map content onto ordinary MDI layers as the mapping framework
  evolved.
- Updated the project and artifact spelling from `mdi_radar` to `mdi-radar`.
- Updated the framework dependency to the released MDI 1.2.3 used by the final
  reference-book manuscript.

### Fixed

- Restored the ETOPO5 visibility toggle after the layer-rendering refactor.
- Made the target-altitude legend size itself from its actual font and labels,
  preventing clipping on different platforms.
- Made the native window-close button behave consistently with Quit.

### Documentation & Testing

- Documented the application workflow, illustrative-data limitations,
  line-of-sight model, and extension architecture.
- Added round-trip, central-longitude, wrapping, and seam tests for the custom
  Plate Carrée projection.

[Unreleased]: https://github.com/heddle/mdi-radar/compare/v1.0.0...develop
[1.0.0]: https://github.com/heddle/mdi-radar/releases/tag/v1.0.0
