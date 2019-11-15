<template>
  <div class="main">
    <header class="header">
      <img class="logo" src="../assets/logo.png" />
      <input class="search-bar" placeholder="역명을 검색해보세요!" />
    </header>
    <MetroMap></MetroMap>
  </div>
</template>

<script>
import MetroMap from "./MetroMap";
export default {
  components: {
    MetroMap
  }
};
</script>

<style scoped>
.logo {
  max-height: 60px;
  max-width: 60px;
}

.header {
  position: fixed;
  border: 1px solid;
  display: flex;
  justify-content: center;
  align-items: center;
  left: 0px;
  top: 0px;
  height: 80px;
  width: 100%;
  z-index: 10;
}

.search-bar {
  margin: 0 20px;
  border: none;
  border-radius: 100px;
  background-color: #bbb;
  font-size: 16px;
  font-weight: bold;
  padding: 16px;
  color: #333;
  padding-top: 15px;
  text-align: center;
}

.search-bar::placeholder {
  font-weight: bold;
}
</style>
