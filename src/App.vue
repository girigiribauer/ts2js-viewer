<template>
  <div id="app">
    <h1 class="title">TypeScript to JavaScript Viewer</h1>
    <Viewer class="viewer" />
  </div>
</template>

<script>
import Viewer from './components/Viewer.vue'

export default {
  name: 'app',
  components: {
    Viewer,
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
.title {
  margin: 0;
  vertical-align: middle;
}
.logo {
  width: 4.5em;
  vertical-align: middle;
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
  display: flex;
  flex-direction: column;
  padding: 1rem;
  box-sizing: border-box;
}
.viewer {
  margin-top: 1rem;
}
</style>
