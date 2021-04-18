<template>
  <div id="map" class="Map"></div>
</template>
<script>
import 'ol/ol.css';
import Map from 'ol/Map';
import View from 'ol/View';
import { defaults as defaultControls, ScaleLine } from 'ol/control';
import { Tile as TileLayer, Vector as VectorLayer } from 'ol/layer';
import { OSM, Vector as VectorSource } from 'ol/source';

export default {
  async mounted() {
    await this.initiateMap();
  },
  methods: {
    initiateMap() {
      const source = new VectorSource();
      const vector = new VectorLayer({
        source: source,
      });
      // Create title layer
      const raster = new TileLayer({
        source: new OSM(),
      });
      // Create map with 2 layers
      new Map({
        controls: defaultControls().extend([
          new ScaleLine({
            units: 'degrees',
          }),
        ]),
        target: 'map',
        layers: [raster, vector],
        view: new View({
          projection: 'EPSG:4326',
          center: [0, 0],
          zoom: 2,
        }),
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.Map {
  position: absolute;
  margin: 0;
  padding: 0;
  height: 500px;
  width: 99%;
}
</style>
