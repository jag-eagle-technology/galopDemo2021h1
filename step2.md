1. Follow the instructions at https://developers.arcgis.com/javascript/latest/display-a-custom-basemap-style/ to display the nz topographic vector basemap item id **734c12e9904b4a8086d2dff8582a93a1** (name the layer variable topoLayer) and the NZ hillshade layer **38c860f8dbd24820b2a59ccc9a3dabdb** (name the variable hillshadeLayer). Don't set the transparency of the vector layer.
2. Update the center property of your map to the Tararuas (NZTM Coordinates)
    a. update your require function to import the point class
    ```
        require([
            "esri/config",
            "esri/Map",
            "esri/views/MapView",
            "esri/Basemap",
            "esri/layers/VectorTileLayer",
            "esri/layers/TileLayer",
            "esri/geometry/Point"
        ], function (
            esriConfig,
            Map,
            MapView,
            Basemap,
            VectorTileLayer,
            TileLayer,
            Point
        ) {
    ```
    b. update the center property of your map to a new point with the NZTM coordinates you wish to center your map on:
    ```
    center: new Point({ x: 1795999, y: 5457405, spatialReference: { wkid: 2193 } }),
    ```
    3. Follow the instructions at https://developers.arcgis.com/javascript/latest/add-a-feature-layer/ to display the following layers:
    | Description | URL             |
    | ----------- | --------------- |
    | Doc Tracks  | https://services1.arcgis.com/3JjYDyG3oajxU6HO/arcgis/rest/services/DOC_Tracks/FeatureServer |
    | Doc Huts    | https://services1.arcgis.com/3JjYDyG3oajxU6HO/arcgis/rest/services/DOC_Huts/FeatureServer   |

    Instead of using map.add you can create define the layers before you create the map and then include them in the map's layer array:

    ```
    const map = new Map({
        basemap: basemap2d,
        layers: [trailsLayer, hutsLayer]
    });
    ```