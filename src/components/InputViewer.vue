<template>
  <div class="input-viewer">
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
    }, 1800),
  }
}
</script>

<style scoped>
.input-viewer {
  flex: 1 1 100%;
  width: 100%;
  margin-top: 0.25rem;
}
textarea {
  width: 100%;
  height: 100%;
  padding: 0.25rem 1rem;
  box-sizing: border-box;
  font-size: 1rem;
  line-height: 1.5;
  resize: none;
}
</style>
