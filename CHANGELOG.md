# Change Log

## Unreleased

### Changes
- Idle handlers no longer defer to scene-graph parents.  Parents still wait for all children to be idle

## Version 0.19.4

### Improvements
- Speed up rebuilding webgl point features (#994)

## Version 0.19.3

### Features
- Layers that use webgl renderers automatically share contexts when possible.  Layers can switch renderers manually as well.  This largely avoids the limitation of number of webgl contexts in a browser (#975)
- Support affine transforms in the proj4 string (#986)

### Improvements
- Speed up rendering geojson features by using constant values for constant geojson styles (#987)

### Changes
- The point clustering radius value is now in display pixels (#983)

### Bug Fixes
- Fixed drawing partial fixed-scale canvas quads (#985)

## Version 0.19.2

### Improvements
- Make fewer function calls when computing polygon strokes (#980)
- Speed up coordinate transforms that only switch y-axis (#979)

## Version 0.19.1

### Features
- Polygon annotations can be drawn in the same continuous smooth manner as line annotations. (#976)

### Changes
- Rename the d3 renderer to svg.  d3 still works as an alias (#965)
- Rename the vgl renderer to webgl.  vgl still works as an alias (#965)

## Version 0.19.0

### Features
- Feature selection API is now enabled automatically if any event handlers are bounds to the feature (#921)
- Added a VTK.js renderer which supports a point feature (#893, #953)

### Improvements
- Coordinate transforms on flat arrays are now faster (#939)
- `convertColor` is memoized to speed up repeated calls (#936)
- All features have a `featureType` property (#931)
- When changing geometry sizes, buffers are reallocated less (#941)
- Initial rendering webGL features is somewhat faster (#943)
- WebGL point and polygon features no longer clip by z coordinates (#963)

### Changes
- Removed the dependency on the vgl module for the `object` and `timestamp` classes (#918)
- CSS color names are obtained from an npm package rather than being defined in the util module (#936)
- Updated several npm modules (#944)
- Report the unmasked renderer used with webgl (#947)
- Width and height are now in the base renderer class (#962)

### Bug Fixes
- Fixed some minor issues with layers (#949)

### Documentation
- Improve documentation (#922, #928, #929, #930, #932, #948, #950, #951, #956, #960, #961)
- Added a point cluster example (#957)
- Editor tutorials keep history in browser (#926)

## Version 0.18.1

### Bug Fixes
- Fixed an issue with the annotation key handler (#923)

## Version 0.18.0

### Features
- Added an idle property to objects (#894)
- Better handling and changing of camera clipbounds (#899)
- File readers (the geojsonReader) now returns a Promise.  The layer will report that it is not idle until this promise is finalized (#905)

### Bug Fixes
- Fixed an issue with overlapping, cropped tiles on old browsers (#901)
- Fixed an issue where a `geo.gl.polygonFeature` could be updated after it was deleted (#913)

### Changes
- Changed build process: optional dependencies are now included in the bundle by default (#890)
- Transpile with Babel to support old browsers and new language features (#900, #903)
- The geojsonReader has been renamed from `jsonReader` to `geojsonReader`.  The old name still works as an alias (#905)
- Catch errors in animation frame callbacks (#911)

## Version 0.17.0

### Features
- Add multi-color support to the continuous color legend (#810)
- Warn when trying to create an unsupported feature (#823)
- Expose registries (#830)
- Add all proj4 projections (#840, #873)
- Trigger an event when an annotation's coordinates change (#841)
- Add an option to limit text feature rendering (#834)
- Calculating min and max of array is now a utility function (#835)
- Generalized meshes (#817)
- Added a `wrapAngle` utility function (#836)
- Isolines (#838)

### Bug Fixes
- Ensure GL polygons are built once before their strokes so that the strokes are always on top (#806)
- Work around `atan` bugs in openmesa and swiftshader WebGL renderers (#816)
- Fix text alignment on the scale widget (#828)
- Ignore z values in `vgl.lineFeature` (#833)
- Don't modify geojson object coordinates (#848)
- Ensure all point position calls pass the data index (#852)

### Testing
- Test with a muted video (#811)
- Use Firefox headless (#818)
- Use karma-spec-reported for better output (#829)
- Upgrade jasmine (#837)
- Refactor how external data is fetched (#851)
- Add more support for testing examples, similar to tutorial tests (#866)
- Refactored the server script to allow serving the website and build directories as well as the dist directory (#868)

### Documentation
- Improve tutorial page layout (#809)
- Improve documentation (#819, #825, #824, #839, #844, #849, #859, #858, #867, #872)
- Update tutorials when text is deleted (#827)
- Added a rainfall example with isolines and contours (#869)
- Change the Deep Zoom example to make it more generic and use a public data source (#875)
- Automate website deployment (#877)

### Changes
- Remove bower support (#856)
- Switch to webpack v3 (#854)
- Removed needless function wrappers (#870)

## Version 0.16.0

### Features
- Events allow changing feature order on mouse over and mouse click (#807)

### Improvements
- Multiple UI layers can be active at once (#802)
- Clear animation queue when the map is destroyed (#801)
- Handle dereferencing errors in screenshots more gracefully (#803)

### Changes
- Line style function parameters are more consistent (#804)

### Bug Fixes
- Polygon strokes were sometimes drawn under polygon fills (#806)

### Documentation
- Added a [line tutorial](https://opengeoscience.github.io/geojs/tutorials/lines) (#805)

## Version 0.15.2

### Features
- Allow specifying the map's initial maximum bounds in a different GCS (#794)
- Improve setting widget positions (#796)
- Add methods to simplify line geometries (#791)
- Add functions computing spherical and Vincenty distances (#797)
- Add a scale widget (#798)
- Improve the screenshot function by dereferencing CSS urls (#799)

### Testing
- Fix testing with Chrome 65 (#792)
- Add tests for geo.gui.widget and geo.gui.domWidget (#795)

### Documentation
- Enable the [color legend example](https://opengeoscience.github.io/geojs/examples/color-legend/) (#790)
- Add a new [editor tutorial](https://opengeoscience.github.io/geojs/tutorials/editor3) with HTML and CSS panes (#783)
- Use https urls for openstreetmap tiles in all examples and tutorials (#793)

## Version 0.15.1

### Testing
- Use resemblejs for testing rather than node-resemble (#785)

### Packaging
- Resolve hammerjs by it's name on npm in addition to the global variable `Hammer` (#787)

## Version 0.15.0

### Features
- Individual annotations can be edited (#769)

### Improvements
- Sped up updating line features (#779)

### Bug Fixes
- Fixed hit test on closed lines (#780)
- Fixed mouse buttons reporting on Firefox (#782)

## Version 0.14.0

### Features

- Added an `object.geoIsOn` function to check if an event is bound (#768)
- Use the average perimeter for the center of a polygon or line (#761)
- Allow display to/from gcs conversion functions to handle arrays of points (#766)
- When drawing a line annotation, don't create intermediate colinear points (#759)
- Improve exiting and reloading maps (#750)
- Various minor improvements (#767, #760)

### Packaging
- Refactored importing optional dependencies so webpack makes them truly optional (#770)
- Upgraded to jQuery 3.x (#772, #773)
- Updated npm packages (#756)
- Reduce packaging effects (#763, #751)

### Testing
- Improved testing with different browsers (Chrome 64 and Firefox 58) (#775, #771, #755)

### Bug Fixes
- Include stroke widths when doing a point search on polygons (#762)
- Fixed `pointSearch` when the feature used a non-default gcs (#758)
- Fixed unbinding keyboard events (#757)

### Tutorials and Website
- Added more tutorials (#774)
- Minor website improvements (#753, #752)

## Version 0.13.0

### New features
- Added a new video quad feature (#745)
- Annotation id's are now persevered when reloading geojson (#747)

### Bug fixes
- Fixed setting rotation on map creation (#740)
- Fixed polygon fill and opacity interaction (#744)
- Fixed handling GCS in geojson annotation imports (#748)

### Improvements to the website and documentation
- Updated GeoJS's [website](https://opengeoscience.github.io/geojs/) (#729)
- Improved the [API documentation](https://opengeoscience.github.io/geojs/apidocs/) (#738)
- Added an "editor" [tutorial](https://opengeoscience.github.io/geojs/tutorials/) (#742)
- Updated some [examples](https://opengeoscience.github.io/geojs/tutorials/) (#743)

## Version 0.12.4

- Added a new color legend widget (#731)
- Fixed `z-index` bug on new layers (#732)
- Improved testing infrastructure (#735, #737)
- Removed some boiler plate code from the examples (#733)

## Version 0.12.3

- Added annotation labels (#719)
- Added text feature (#719)
- Added tutorial infrastructure and some simple tutorials (#725, #727, #728)
- Handle tap-touch actions (adds support for some tablet styluses) (#730)

## Version 0.12.2

- Started revamping our [API documentation](https://opengeoscience.github.io/geojs/apidocs/) with a new template (#704, #706, #708, #710, #713)
- Several minor API improvements (#707)
- Added subdomain template parameters for tile layer urls (#715)

## Version 0.12.1

- Fix bugs in rectangle annotations (#693, #694)
- Add new optimized methods for updating styles of features for animations and a new [example](https://opengeoscience.github.io/geojs/examples/animation/) (#687)
- Fix checks for optional dependencies (#696)
- Change the template for our [apidocs](https://opengeoscience.github.io/geojs/apidocs/) to [jaguarjs-jsdoc](https://github.com/davidshimjs/jaguarjs-jsdoc) (#697)
- Fix a bug in applying polygon stroke styles (#700)

## Version 0.12.0

- Handle basic touch interactions using hammerjs (#675)
- Increase testing coverage (#676, #677, #684)
- Support additional line styling options in the json reader (#680)
- Add the ability to draw line annotations (#681)
- Add `visible` and `selectionAPI` methods to layers (#682)
- Replace custom quad tree implementation with kdbush (#685)
- Remove several unused utility methods (#686)
- Move vgl mocking function into `utils` for use in upstream testing (#688)

## Version 0.11.1

- Added a `map.screenshot` method to take screenshots of the current map view (#665, #667)
- Added a screenshot button on the example pages (#669)
- Made it easier to disable or replace keyboard actions in the interactor (#670)

## Version 0.11.0

- Refactored GL line feature with a number of new styling options available.  See our [blog post](https://blog.kitware.com/drawing-lines-in-geojs/) and the new [line example](https://opengeoscience.github.io/geojs/examples/lines/) for more details.  (#649, #662)
- Added keyboard shortcuts for map navigation.  (#661)
- Most DOM styling is now done with a CSS file rather than setting inline styles.  (#660)
- Added GCS options to the annotation interface.  (#654)
- Added headless unit testing for GL code and examples.  (#651, #658).
- Removed unused source files.  (#656, #657)

## Version 0.10.5

- Made annotation states more consistent (#643)
- Reduced lag between layers (#644)
- Fixed gaps between tiles (#648)
- Fixed map jumping after certain transitions (#650)

## Version 0.10.4

### Changes
- Added a pixelmap feature and [example](https://opengeoscience.github.io/geojs/examples/pixelmap/) (#637)
- The location with a quad is reported in mouse events and point search functions (#635)
- Canvas elements can be rendered in quads on the canvas renderer (#634)
- Most features support visibility (#632)
- Colors can be specified with a greater variety of css methods, such as `rgb()` and `rgba()` (#636)
- Point annotations can scale with zoom (#628)

## Version 0.10.3

### Changes
- Fixed a bug in getting the visible bounds using a custom map projection (#625)
- Slider widgets can now be repositioned and resized (#619)
- Improved the annotation API with the ability to import and export GeoJSON (#617)

## Version 0.10.2

### Changes
- Add a closed flag for line features (#602)
- Minor changes and bug fixes in the interactor (#603, #604, #605)
- Allow showing partial tiles on edges (#606)
- Minor fixes to geojson rendering (#609)
- Update to VGL 0.3.10 (#608, #612)
- Reduce flickering in point cluster rendering (#621)
- Beta support for interactive annotations and a new [example](https://opengeoscience.github.io/geojs/examples/annotations/) (#613, #616)

## Version 0.10.1

### Bug fixes
- Fixed a bug preventing deletion of stroked polygons (#601)

## Version 0.10.0

### Breaking changes
- Removed the `planeFeature` class in favor of the faster and more powerful`quadFeature` (#583)
- Changed the callback signature for the `fill` style, which turns on or off rendering the polygon fill (#597)

### Additions and improvements
- Improved heatmap feature and [example](https://opengeoscience.github.io/geojs/examples/heatmap/) (#574, #577, #578, #579)
- Replaced grunt build tasks with webpack and npm scripts (#580)
- Added a d3 rendered `quadFeature` (#581)
- Added selection-based zoom (#582)
- Added an interface for `createLayer` to request renderers by feature support (#590)
- Improved polygon rendering performance  ([massively](https://github.com/OpenGeoscience/geojs/pull/594#issuecomment-226821131)) and added a usage [example](https://opengeoscience.github.io/geojs/examples/polygons/) (#594)
- Added an [example](https://opengeoscience.github.io/geojs/examples/sld/) of customizing the style of WMS layers (#595)
- Added stroking to the polygon feature (#597)

### Bug fixes
- Fixed a bug in box selection with map rotation (#582)
- Fixed the `draw` method on GL and canvas features (#585)
- Fixed a rendering bug in GL line features (#597)
- Removed the [now unavailable](http://devblog.mapquest.com/2016/06/15/modernization-of-mapquest-results-in-changes-to-open-tile-access/) mapquest tile servers from the examples (#598)

## Version 0.9.1

### Changes
- Added a new [heatmap](https://opengeoscience.github.io/geojs/examples/heatmap/) feature (#557)
- Switched to [earcut](https://github.com/mapbox/earcut) for triangulating polygons (#555)
- Added methods on `geo.transform` to load EPSG projections from [epsg.io](http://epsg.io/) (#561)
- Recorded the git SHA at build time as `geo.sha` (#562)
- Made `tileLayer.tilesAtZoom` configurable to support rectangular images (#568)
- Added caching to proj4 transform objects (#570)
- Added jQuery to the distributed bundle (#572)

## Version 0.9.0

### New features
- Added a canvas renderer for tile layers and quad features
- Added new marker styles for d3 rendered vectors
- Zooming with the mouse wheel now supports animation and momentum (see the updated [Tiles](https://opengeoscience.github.io/geojs/examples/tiles/) example)
- All files have been converted into CommonJS modules and are built with [webpack](https://webpack.github.io/)
- PhantomJS tests are now executed with the [Karma test runner](https://karma-runner.github.io/0.13/index.html)
- Unit test coverage information is collected by [istanbul](https://gotwarlost.github.io/istanbul/) and reported to [codecov](https://codecov.io/github/OpenGeoscience/geojs?branch=master)
- Performance results are submitted to CDash during testing as a JSON-encoded "notes" file ([example](https://my.cdash.org/viewNotes.php?buildid=936301))

### Bug fixes
- Fixed several bugs related to map animations and transitions
- Fixed a tile layer performance bug when `keepLower=false`

### Breaking changes
- The global `inherit` function has moved to `geo.inherit`
- The released bundle (`geo.js`) now includes **pnltri**, **proj4**, and **gl-matrix** internally
- The external bundle (`geo.ext.js`) now contains only **jQuery** and **d3**
- All sources in `src/core/` have moved up a directory to be consistent with the namespaces in the module
- The jQuery plugin has moved to [OpenGeoscience/geojs-jquery-plugin](https://github.com/OpenGeoscience/geojs-jquery-plugin) and [geojs-jquery-plugin](https://www.npmjs.com/package/geojs-jquery-plugin) on npm

## Version 0.8.0

### Major changes
- Quad features have been created as a replacement for plane features.  They can draw multiple convex quadrilaterals with images or solid colors as textures within a single feature instantiation.  These features also support default styles or images that display while asynchronous resources load.
- A new [quad example](https://opengeoscience.github.io/geojs/examples/quads/) demonstrates the new capabilities of the quad feature.
- A new [reprojection example](https://opengeoscience.github.io/geojs/examples/reprojection/) demonstrates how quad features can be used to reproject a standard tile layer.  It also provides an additional example of using mouse events on point features to display textual information in a popup box and to recenter the map on click.
- UI Layers will now automatically remain on top when adding new layers.
- Migrated to [ESLint](https://eslint.org/) from jshint/jscs for style checking.

### Performance improvements

Migrating from the plane feature to the new quad feature provides major performance gains for the GL tile layer.  @manthey provided some [benchmarks](https://github.com/OpenGeoscience/geojs/pull/528#issuecomment-180411371) in his PR demonstrating how much this improves performance on a variety of platforms.  Here is an summary of the improvements he measured:

| Test | Average frame (ms) | Slow frames (%) | Worst frame (ms) |
| --- | --- | --- | --- |
| desktop-chrome-plane | 12.69 | 24.59 | 84.9 |
| desktop-chrome-quad | 3.31 | 0.44 | 20.74 |
| destop-firefox-plane | 55.25 | 55.52 | 1316.73 |
| destop-firefox-quad | 7.5 | 3.82 | 41.04 |
| laptop-chrome-plane | 25.55 | 60.21 | 157.15 |
| laptop-chrome-quad | 3.89 | 3.31 | 62.62 |
| laptop-firefox-plane | 130.04 | 95.71 | 1126.31 |
| laptop-firefox-quad | 21.92 | 91.1 | 67.21 |

## Version 0.7.0

### New features
- Maps can now be rotated either through the [javascript API](https://github.com/OpenGeoscience/geojs/blob/release-0.7.0/src/core/map.js#L416-L426) or by pressing `Ctrl` while dragging or using the mouse wheel.
- The Tile Layer example allows turning on or off rotations or restricting rotations to specific orientations.
- A new renderer fallback API supports querying support for a renderer and falling back to a different supported renderer.  The default OSM layer now supports this mechanism falling back to a raw HTML interface when webGL is not available.

### Bug fixes
-  The [Deepzoom example](https://opengeoscience.github.io/geojs/examples/deepzoom/) was mistakenly using the HTML renderer.
- Fixed several race conditions involved in loading and purging tiles
- The tile cache will now automatically grow when it is not large enough to contain all of the tiles in use

### Testing
- Unit tested code coverage is now up to 62% from 42% at version 0.6.

## Version 0.6.0

### New features and API additions
- Completely new tile layer class that moves formally GL specific code into core
  - Maps no longer require GL or even a base layer
  - Support for SVG and HTML rendering for tile layers
  - Support for arbitrary [PROJ4](http://proj4js.org/) projection strings
  - Support wrapping tiles both horizontally and vertically for periodic images
  - Tiles can be an arbitrarily sized rectangle
  - Hooks for dynamically generated tiles rather than just static images
  - The definition of "zoom level" is now consistent with the use in other libraries
- New camera class used to keep track of the visible area and world to image space conversions
- General support for image pyramids through the tile layer (including [medical imaging](https://opengeoscience.github.io/geojs/examples/deepzoom/))
- [Choropleth](https://opengeoscience.github.io/geojs/examples/choropleth/) feature type
- New API for [widgets](https://opengeoscience.github.io/geojs/examples/widgets/)
- New [example](https://opengeoscience.github.io/geojs/examples/tiles/) showing off the features available for tile layers
- GeoJSON reader now supports [Polygon](http://geojson.org/geojson-spec.html#polygon) and [Multipolygon](http://geojson.org/geojson-spec.html#multipolygon) geometries
- Layers can now be reordered dynamically
- Added a new mouse event (`click`) that detects mouse clicks on the map canvas
- The map interactor can be disabled temporarily to cede control of the mouse and keyboard events to external handlers
- Support for subdomains in tile url template strings
- Opacity controls are now supported by all layer types
- Map "origin" parameter provides a fixed offset for world coordinates to support higher precision at high zoom levels
- New map option (`clampZoom`) to limit zoom levels to a given range
- New `osmLayer` option (`tileRounding`) to control which tiles are loaded at non-integer zoom levels

### API changes
- Web mercator (`EPSG:3857`) coordinates are now in units of meters rather than degrees
- Lower resolution tiles are loaded before high resolution tiles
  - Creates the perception of faster load times
  - Greatly reduces the occurrence of background visibility while tiles load
- Removed the per-layer geographic projection attribute (`layer.gcs`) that was never fully implemented
  - Every layer is now expected to render in the map's world coordinate system
  - Feature layers can define a "local" coordinate system that is used internally
  - Tile layers have an additional coordinate system defined for each displayable zoom level
- Removed `geo.mercator` in favor of a generic projection class based on PROJ4
- Tile URL template strings now use the more common curly brackets (`{x}`) rather than angle brackets (`<x>`)
- Nearly all of the internals of the `osmLayer`

### Performance
- A tile fetch queue now prioritizes downloaded tiles by what is currently in view
- Mouse event handlers are now throttled to fire at most every 30 ms
- Compiled GL shaders are now cached and shared between features
- Configurable tile cache size

### Testing
- A new library of "mocked" classes has been started to mock interfaces between the classes inside unit tests.
- All new core classes have unittest coverage over 80% and many more classes now have coverage over 50%

| File | Cov | File | Cov | File | Cov |
| :-- | :-- | :-- | :-- | :-- | :-- |
| event.js | 100.0% | tileLayer.js | 96.2% | mapInteractor.js | 79.7% |
| osmLayer.js | 100.0% | tile.js | 96.1% | renderer.js | 71.4% |
| tileCache.js | 100.0% | object.js | 90.4% | layer.js | 70.8% |
| timestamp.js | 100.0% | sceneObject.js | 87.3% | featureLayer.js | 69.0% |
| version.js | 100.0% | planeFeature.js | 87.0% | init.js | 66.3% |
| fetchQueue.js | 100.0% | imageTile.js | 81.8% | map.js | 55.7% |
| camera.js | 97.7% |  |  |  |  |

### Infrastructure and building
- Continuous coverage reporting of unit tests submitted to [CDash](https://my.cdash.org/index.php?project=geojs)
- VGL submodule removed in favor of inclusion via bower
- Support for installing as the `root` user
- Data used for testing and examples are now hosted at [data.kitware.com](https://data.kitware.com/)
- The library is no longer built automatically after `npm install` to fix [downstream build problems](https://github.com/OpenGeoscience/geojs/pull/461).

### Bug fixes
- Setting camera bounds now uses the correct coordinate system
- GeoJSON polygon features no longer rendered as lines
- Discrete zoom now works with touch-like devices
- The `planeFeature` now handles coordinate transformations
- Rendering operations (such as loading new tiles) now occur during map navigation and transition events

### Known issues
- Several [performance problems](https://github.com/OpenGeoscience/geojs/issues?utf8=%E2%9C%93&q=label%3Aperformance+) have been exposed by rendering new tiles during map navigations
  - Many garbage collections occur during mouse handlers due to excessive memory allocations
  - Shader programs are not shared among tiles so they need to be linked for each tile

### Contributors
- @aashish24
- @danlamanna
- @dcjohnston
- @jbeezley
- @manthey

Huge thanks to all of the contributers, and the many others who tested, created issues, and gave feedback during the development of this release.


## Version 0.5.0

### New features
- Contour feature for generating [contour plots](https://opengeoscience.github.io/geojs/examples/contour/) from gridded data
- Hierarchical data clustering with an experimental option for clustered point features
- Multipolygon support in the GeoJSON reader
- Support for rendering with parallel projection along with discrete zooming and image to device pixel alignment
- Per layer attribution notices as well as default attributions for OpenStreetMap
- Support for drawing multiple maps on a single web page
- Support for authenticated tile servers via `crossOrigin = "use-credentials"`

### Breaking changes
- Zoom level is now consistent with other mapping libraries
- Removed `geo.latlng`
- Changed default feature colors
- Map nodes are now created as `position: relative`

## Version 0.4.2

- New examples added showing [map transitions](https://opengeoscience.github.io/geojs/examples/transitions/) and [data animation](https://opengeoscience.github.io/geojs/examples/dynamicData/)
- Large performance improvement for point feature mouse handler setup
- Removed jquery-mousewheel dependency
- Toggling feature visibility now toggles mouse handlers as well
- JQuery plugin will now accept constant values for point sizes and will no longer reset the global gl variable

## Version 0.4.1

- Fixes the built library included in the repository so that it contains vgl

## Version 0.4.0

- Updated to 0.4.0 because npm versions are immutable (the previous geojs was published up to 0.3.x)
- Minor changes to the build process to make `npm install` work

## Version 0.2.0

## Version 0.1.0

- First Release
