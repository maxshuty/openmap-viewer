<template>
  <map-comp />
</template>

<script>
import MapComp from './components/MapComp.vue';
export default {
  name: 'App',
  components: { MapComp },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
