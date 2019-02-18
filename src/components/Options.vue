<template>
  <div class="options">
    <label v-for="(target, key) in targets" :key="key">
      <input v-model="targets[key]" type="checkbox"> {{ targetLabels[key] }}
    </label>
  </div>
</template>

<script>
export default {
  name: 'Options',
  props: [
    'targets',
    'targetLabels',
  ],
}
</script>

<style scoped>
.options {
  border: 1px solid #fff;
  text-align: left;
}
.options label {
  display: inline-block;
  margin-right: 0.75rem;
  padding: 0.5rem;
  user-select: none;
}
</style>
