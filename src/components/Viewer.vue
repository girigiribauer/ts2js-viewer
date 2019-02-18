<template>
  <div class="viewer">
    <div class="split">
      <InputViewer @writtenCode="writtenCode" />
    </div>
    <template v-for="(target, key) in targets">
      <div class="split" v-if="target" :key="key">
        <OutputViewer :output="output[key]" :target="key" />
      </div>
    </template>
  </div>
</template>

<script>
import * as ts from "typescript";
import InputViewer from '@/components/InputViewer.vue'
import OutputViewer from '@/components/OutputViewer.vue'

export default {
  name: 'Viewer',
  props: [
    'targets'
  ],
  data: function() {
    return {
      code: '',
    };
  },
  methods: {
    writtenCode(src) {
      this.code = src;
    },
  },
  computed: {
    output: function() {
      // eslint-disable-next-line
      console.log('updated output');

      let results = {};

      Object.entries(this.targets).forEach(([key, value]) => {
        if (!value) {
          results[key] = '';
          return;
        }
        const result = ts.transpileModule(this.code, {
          compilerOptions: {
            target: ts.ScriptTarget[key],
            module: ts.ModuleKind.CommonJS
          }
        });
        results[key] = result.outputText;
      });

      return results;
    }
  },
  components: {
    InputViewer,
    OutputViewer,
  },
}
</script>

<style scoped>
.viewer {
  display: flex;
  flex-direction: row;
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  margin-right: auto;
  margin-left: auto;
  overflow: scroll;
}
.split {
  margin-left: 1rem;
  flex: 1 1 calc(50% - 0.5rem);
}
.split:first-child {
  margin-left: 0;
}

</style>
