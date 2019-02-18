<template>
  <div class="output-viewer">
    <h2>Output (JavaScript: {{ target }})</h2>
    <textarea disabled v-model="output"></textarea>
  </div>
</template>

<script>
export default {
  name: 'OutputViewer',
  props: [
    'output',
    'target'
  ]
}
</script>

<style scoped>
.output-viewer {
  display: flex;
  flex-direction: column;
  flex: 1 1 100%;
  width: 100%;
  height: 100%;
}
h2 {
  margin: 0;
  font-size: 1rem;
  line-height: 1.5;
  text-align: left;
}
textarea {
  flex: 1 1 100%;
  width: 100%;
  margin-top: 0.25rem;
  padding: 0.25rem 0.5rem;
  box-sizing: border-box;
  font-size: 1rem;
  font-family: monospace;
  line-height: 1.5;
  resize: none;
}
</style>
