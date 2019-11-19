<template>
  <div>
    <Search id="search-bar" />
    <Map />
  </div>
</template>

<script>
import Search from "@/components/Search";
import Map from "@/components/Map";

export default {
  components: {
    Search,
    Map
  }
};
</script>
