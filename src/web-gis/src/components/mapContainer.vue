<template>
  <div id="mapcontainter">

  </div>
</template>

<script>
import { loadModules, loadCss } from 'esri-loader'
export default {
  name: "mapcontainer",
  props: {
    msg: String
  },
  mounted() {
    loadCss('http://192.168.0.218/arcgis_js_v411_api/arcgis_js_api/library/4.11/esri/themes/light/main.css');         //'http://47.107.229.70:8411/esri/css/main.css' https://js.arcgis.com/4.12/esri/themes/light/main.css
    const options = { url: 'http://192.168.0.218/arcgis_js_v411_api/arcgis_js_api/library/4.11/init.js' };   //'http://47.107.229.70:8411/init.js'  https://js.arcgis.com/4.12/
    loadModules(['esri/views/MapView', 'esri/Map', "esri/WebScene", 'esri/layers/MapImageLayer', 'esri/layers/VectorTileLayer'], options).then(([MapView, Map, WebScene, MapImageLayer, VectorTileLayer]) => {
    
    
    var map = new Map({
        // layers: [new MapImageLayer({
        //   url: "http://192.168.0.218:6080/arcgis/rest/services/xtm_Map/MapServer",
        // })]
      });
      const webScene = new WebScene({                    // Define the web scene reference
        portalItem: {
          id: "579f97b2f3b94d4a8e48a5f140a6639b",
          portal: "https://www.arcgis.com"               // Default: The ArcGIS Online Portal
        }
      });

      //------------矢量切片图层
      var vtlLayer2 = new VectorTileLayer({
        // URL to the style of vector tiles
        url: "https://www.arcgis.com/sharing/rest/content/items/4cf7e1fb9f254dcda9c8fbadb15cf0f8/resources/styles/root.json"
      });
      var vtlLayer = new VectorTileLayer({
        // URL to the vector tile service
        url: "https://basemaps.arcgis.com/arcgis/rest/services/World_Basemap_v2/VectorTileServer"
      });

      map.layers.add(vtlLayer);
      var view = new MapView({
        map: map,
        container: 'mapcontainter',
        center: [112, 26],          // The center of the map as lon/lat
        zoom: 14                      // Sets the zoom level of detail (LOD) to 13
      });
    }).catch(err => {
      console.error(err);
    });

  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
#mapcontainter {
  width: 100%;
  height: 100%;
}
</style>
