<template>
  <v-app id="search-tab">
    <div>
      <v-autocomplete
        class="search-bar"
        label="역명 검색"
        v-model="selected"
        :items="stations"
        @change="searchChanged"
      >
      </v-autocomplete>
    </div>
  </v-app>
</template>

<script>
import * as metro_data from "@/metro_data.json";

export default {
  data: () => ({
    metroData: metro_data.default.seoulMetro,
    stations: [],
    selected: ""
  }),
  methods: {
    searchChanged() {
      this.$store.state.searching = this.selected;
    }
  },
  mounted() {
    for (let station of this.metroData) {
      this.stations.push(station.line + " " + station.stationName);
    }
  }
};
</script>

<style scoped>
.search-bar {
  margin: 10px 10px 0 10px;
}

#search-tab {
  height: 80px;
}
</style>
