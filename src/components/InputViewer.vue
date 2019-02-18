<template>
  <div class="input-viewer">
    <h2>Input (TypeScript)</h2>
    <textarea v-model="code" placeholder="TypeScript code here!"></textarea>
  </div>
</template>

<script>
import { debounce } from 'debounce';

export default {
  name: 'InputViewer',
  data: function() {
    return {
      code: '',
    };
  },
  props: [
    'writtenCode',
  ],
  watch: {
    code: debounce(function(value) {
      this.$emit('writtenCode', value);
    }, 1300),
  }
}
</script>

<style scoped>
.input-viewer {
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
