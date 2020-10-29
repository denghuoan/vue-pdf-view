<template>
  <div id="app">
    <!-- <VuePdfPages></VuePdfPages> -->
    <!-- <VuePdfAll></VuePdfAll> -->
    <!-- <PdfJsPublic></PdfJsPublic> -->
    <PdfJsServer></PdfJsServer>
  </div>
</template>

<script>
import VuePdfPages from './components/VuePdfPages'
import VuePdfAll from './components/VuePdfAll'
import PdfJsPublic from './components/PdfJsPublic'
import PdfJsServer from './components/PdfJsServer'
export default {
  name: 'App',
  components: {
    VuePdfPages,
    VuePdfAll,
    PdfJsPublic,
    PdfJsServer
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
