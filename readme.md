https://www.mapbox.com/

https://www.qgis.org/en/site/forusers/download.html

# What are vector tiles?
## A Brief History of Web Maps
---
###  Static maps
  - Single image rendered on the server
  - Data can be overlayed

<br>

---

### Slippy maps
  ![Slippy Maps](/img/vector_tiles_pyramid_structure.png "Slippy maps")
  - Raster tiles
    - Many images rendered on the server
    - New requests made during navigation
    - Styles must be pre-baked
  - Vector tiles
    - Mathmatical representation of data
        - Very light weight
        - Data embedded with features        
        - *Quickly* stylable
      - Points, lines, polygons
      - .pbf, .mvt, .mbtiles
      - Sliced, serialized (machine readable only) geojson
          ```json
          {
          "type": "FeatureCollection",
          "features": [
              {
              "type": "Feature",
              "properties": {},
              "geometry": {
                  "type": "Point",
                  "coordinates": [-75.179443359375,39.977120098439634]
              }
              },
              {
              "type": "Feature",
              "properties": {},
              "geometry": {
                  "type": "LineString",
                  "coordinates": [
                    [-75.1629638671875,39.95606977009003],
                    [-74.761962890625,40.153686857794035],
                  ]
              }
              },
              {
              "type": "Feature",
              "properties": {},
              "geometry": {
                  "type": "Polygon",
                  "coordinates": [
                  [
                      [-74.9981689453125,39.715638134796336],
                      [-74.4268798828125,39.70718665682654],
                      [-74.53674316406249,40.065460682065535],
                      [-74.9981689453125,39.715638134796336]
                  ]
                  ]
              }
          }
          ```
<br>
<br>

---

# Vector Tiles for Web Apps

## Options for serving:
  - Custom servers
    - https://github.com/sshuair/awesome-gis#web-map-servers
    - qgis server
    - arcgis server
    - postgres
    -...
    - **Requirements:**
      - Dedicated server machine
      - Middleware for API
      - Caching
        - Tegola
        - T-Rex
        - Posttile
        - Postserve
        - Nodejs
        - ...
  - Platform hosted
    - ArcGIS
    - Mapbox
    - Cartodb
## Options for rendering:
  - https://github.com/sshuair/awesome-gis#front-end-framework
  - [Free/Libre Open Source Software](https://www.fsf.org/blogs/rms/20140407-geneva-tedx-talk-free-software-free-society/)
    - Leaflet
    - MapLibre
    - OpenLayers
  - Mapbox
  - ArcGIS
  - Cartodb

<br>

---

# QGIS -> Mapbox Studio -> MapLibre workflow

## QGIS
  - Import layers, style and prepare map
  - For single layer, right click and export layer as geojson
    ![Export single](/img/ExportSingle.png "Export single")
  - For multiple layers use the bulkvectorplugin:
    ![bulkvectorplugin](/img/bulkvectorplugin.png "bulkvectorplugin")
    - Plugins -> Manage and install -> install "bulkvectorexport"
    - Choose Vector -> bulkvectorexport
    ![bulkvectorplugin](/img/bulkvectorplugin-use.png "bulkvectorplugin")
    - Select folder to export to
    ![bulkvectorplugin](/img/bulkvectorplugin-geojson.png "bulkvectorplugin")
## Mapbox Studio
### Upload tileset
  ![mb](/img/mb-1.png "mb")
  ![mb](/img/mb-2.png "mb")
  ![mb](/img/mb-3.png "mb")
  ![mb](/img/mb-4.png "mb")
### Create style
  ![mb](/img/mb-5.png "mb")
  ![mb](/img/mb-6.png "mb")
### Add tilesets to style and style
  ![mb](/img/mb-7.png "mb")
  ![mb](/img/mb-8.png "mb")
### Publish
  ![mb](/img/mb-9.png "mb")
  ![mb](/img/mb-10.png "mb")
## MapboxGL.js
  - https://docs.mapbox.com/api/maps/vector-tiles/
  - Follow first example replacing necessary parts with mapbox info
  - To add a single tileset to existing map
    - Either add in studio
    - Or add it in code
## Leaflet
  - https://leafletjs.com/examples/quick-start/
  - https://github.com/Leaflet/Leaflet.VectorGrid