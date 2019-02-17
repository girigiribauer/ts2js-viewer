<template>
  <textarea readonly v-model="output"></textarea>
</template>

<script>
export default {
  name: 'OutputViewer',
  props: [
    'output',
  ]
}
</script>

<style scoped>
</style>
