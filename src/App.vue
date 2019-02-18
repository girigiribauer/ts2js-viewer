<template>
  <div id="app">
    <h1 class="title">TypeScript to JavaScript Viewer</h1>
    <Options :targets="targets" :targetLabels="targetLabels" />
    <Viewer :targets="targets" />
  </div>
</template>

<script>
import Viewer from './components/Viewer.vue'
import Options from './components/Options.vue'

export default {
  name: 'app',
  components: {
    Viewer,
    Options,
  },
  data: function() {
    return {
      targets: {
        ES3: true,
        ES5: false,
        ES2015: false,
        ES2016: false,
        ES2017: false,
        ES2018: false,
        ESNext: true,
      },
      targetLabels: {
        ES3: 'ES3',
        ES5: 'ES5',
        ES2015: 'ES2015 (ES6)',
        ES2016: 'ES2016 (ES7)',
        ES2017: 'ES2017',
        ES2018: 'ES2018',
        ESNext: 'ESNext'
      }
    }
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  width: 100vw;
  height: 100vh;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  background: #1a4e84;
  width: 100vw;
  height: 100vh;
  min-height: 25rem;
  display: flex;
  flex-direction: column;
  padding: 1rem;
  box-sizing: border-box;
}
.title {
  margin: 0;
  vertical-align: middle;
}
.options {
  margin-top: 1rem;
}
.viewer {
  margin-top: 1rem;
}
</style>
