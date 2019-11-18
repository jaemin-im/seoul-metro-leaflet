<template>
  <div id="map"></div>
</template>

<script>
import L from "leaflet";
import * as metro_data from "@/metro_data.json";

export default {
  data: () => ({
    map: null,
    tileLayer: null,
    metroData: metro_data.default.seoulMetro
  }),
  methods: {
    initIcon() {
      let icons = [];
    },
    initMap() {
      delete L.Icon.Default.prototype._getIconUrl;
      L.Icon.Default.mergeOptions({
        iconRetinaUrl: require("leaflet/dist/images/marker-icon-2x.png"),
        iconUrl: require("leaflet/dist/images/marker-icon.png"),
        shadowUrl: require("leaflet/dist/images/marker-shadow.png")
      });

      this.map = L.map("map", { doubleClickZoom: false });

      this.map.setView([37.5660649, 126.982373], 13);

      for (let station of this.metroData) {
        let icon = L.icon({
          iconUrl: require(`../assets/${station.line}.png`),
          iconSize: [20, 20]
        });
        L.marker([Number(station.longitude), Number(station.latitude)], {
          icon: icon,
          title: station.stationName,
          riseOnHover: true
        })
          .addTo(this.map)
          .bindPopup(station.stationName);
      }

      this.tileLayer = L.tileLayer("http://{s}.tile.osm.org/{z}/{x}/{y}.png", {
        maxZoom: 18
      });

      this.tileLayer.addTo(this.map);
    }
  },
  mounted() {
    this.initMap();
  }
};
</script>

<style scoped>
@import "../../node_modules/leaflet/dist/leaflet.css";
@import "../../node_modules/leaflet.markercluster/dist/MarkerCluster.css";
@import "../../node_modules/leaflet.markercluster/dist/MarkerCluster.Default.css";
#map {
  height: 800px;
  width: 100%;
  z-index: 1;
}
</style>
