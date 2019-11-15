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
    initMap() {
      delete L.Icon.Default.prototype._getIconUrl;

      L.Icon.Default.mergeOptions({
        iconRetinaUrl: require("leaflet/dist/images/marker-icon-2x.png"),
        iconUrl: require("leaflet/dist/images/marker-icon.png"),
        shadowUrl: require("leaflet/dist/images/marker-shadow.png")
      });

      const metroIcon = L.Icon.extend({
        options: {
          iconSize: [24, 24],
          iconAnchor: [12, 12]
        }
      });

      const line1Icon = new metroIcon({
        iconUrl: require("@/assets/one.png")
      });
      const line2Icon = new metroIcon({
        iconUrl: require("@/assets/two.png")
      });
      const line3Icon = new metroIcon({
        iconUrl: require("@/assets/three.png")
      });
      const line4Icon = new metroIcon({
        iconUrl: require("@/assets/four.png")
      });
      const line5Icon = new metroIcon({
        iconUrl: require("@/assets/five.png")
      });
      const line6Icon = new metroIcon({
        iconUrl: require("@/assets/six.png")
      });
      const line7Icon = new metroIcon({
        iconUrl: require("@/assets/seven.png")
      });
      const line8Icon = new metroIcon({
        iconUrl: require("@/assets/eight.png")
      });
      const line9Icon = new metroIcon({
        iconUrl: require("@/assets/nine.png")
      });
      const lineBIcon = new metroIcon({
        iconUrl: require("@/assets/boondang.png")
      });
      const lineSIcon = new metroIcon({
        iconUrl: require("@/assets/sinboondang.png")
      });

      console.log(line1Icon);

      this.map = L.map("map", { doubleClickZoom: false });

      this.map.setView([37.5660649, 126.982373], 13);

      for (let station of this.metroData) {
        let icon;
        switch (station.line) {
          case "1호선":
            icon = line1Icon;
            break;
          case "2호선":
            icon = line2Icon;
            break;
          case "3호선":
            icon = line3Icon;
            break;
          case "4호선":
            icon = line4Icon;
            break;
          case "5호선":
            icon = line5Icon;
            break;
          case "6호선":
            icon = line6Icon;
            break;
          case "7호선":
            icon = line7Icon;
            break;
          case "8호선":
            icon = line8Icon;
            break;
          case "9호선":
            icon = line9Icon;
            break;
          case "분당선":
            icon = lineBIcon;
            break;
          case "신분당선":
            icon = lineSIcon;
            break;
          default:
            break;
        }
        L.marker(
          [parseFloat(station.longitude), parseFloat(station.latitude)],
          { icon: icon, title: station.stationName, riseOnHover: true }
        )
          .addTo(this.map)
          .bindPopup(station.stationName);
      }

      // L.marker([37.566, 126.982]).addTo(this.map);

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
