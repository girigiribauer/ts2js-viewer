<template>
  <div class="viewer">
    <div class="splitter">
      <div class="split split-typescript">
        <h2>Input (TypeScript)</h2>
        <InputViewer @writtenCode="writtenCode" />
      </div>
      <div class="split split-javascript">
        <h2>Output (JavaScript)</h2>
        <OutputViewer :output="output" />
      </div>
    </div>
  </div>
</template>

<script>
import * as ts from "typescript";
import InputViewer from '@/components/InputViewer.vue'
import OutputViewer from '@/components/OutputViewer.vue'

export default {
  name: 'Viewer',
  data: function() {
    return {
      code: '',
      output: '',
    };
  },
  methods: {
    writtenCode(src) {
      const result = ts.transpileModule(src, {
        compilerOptions: {
          module: ts.ModuleKind.CommonJS,
        }
      });

      this.output = result.outputText;
    },
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
  flex-direction: column;
  box-sizing: border-box;
  width: 100%;
  height: 100%;
}
.splitter {
  flex: 1 1 100%;
  display: flex;
  flex-direction: row;
}
.split {
  flex: 1 1 calc(50% - 0.5rem);
  display: flex;
  flex-direction: column;
}
.split + .split {
  margin-left: 1rem;
}
.split h2 {
  margin: 0;
  font-size: 1rem;
  line-height: 1.5;
  text-align: left;
}
.split textarea {
  flex: 1 1 100%;
  width: 100%;
  margin-top: 0.25rem;
  padding: 0.25rem 1rem;
  box-sizing: border-box;
  font-size: 1rem;
  line-height: 1.5;
  resize: none;
}
</style>
