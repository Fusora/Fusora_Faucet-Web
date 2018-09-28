<template>
  <div id="app">
    <Main/>
  </div>
</template>

<script>
import Main from './components/Main.vue'

export default {
  name: 'app',
  components: {
    Main
  }
}
</script>

<style>
#app {
  background: linear-gradient(#005de0, #00c4fb);
  overflow: auto;
  padding: 0;
  margin: 0;
  height: 100%;
  width: 100%;
  position: absolute;
}
</style>
