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
  ![This is a alt text.](/vector_tiles_pyramid_structure.png "This is a sample image.")
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
  - For multiple layers
    - Plugins -> Manage and install -> install "bulkvectorexport"
    - Choose Vector -> bulkvectorexport
    - Select folder to export to
## Mapbox Studio
  - Create style
  - Add tilesets to style
  - Publish
## MapboxGL.js
  - https://docs.mapbox.com/api/maps/vector-tiles/
  - Follow first example replacing necessary parts with mapbox info
  - To add a single tileset to existing map
    - Either add in studio
    - Or add it in code
## Leaflet

