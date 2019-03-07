<template>
  <div class="input-viewer">
    <div class="header-group">
      <h2>Input (TypeScript)</h2>
      <select class="preset" v-model="preset">
        <option value="" default>reset</option>
        <option value="enums">Enums</option>
        <option value="interfaces">Interfaces</option>
        <option value="classes">Classes</option>
        <option value="symbols">Symbols</option>
        <option value="functionTypes">Function Types</option>
        <option value="forOf">for..of</option>
        <option value="unionTypes">Union Types</option>
        <option value="asyncAwait">Async Await</option>
      </select>
    </div>
    <textarea v-model="code" placeholder="TypeScript code here!"></textarea>
  </div>
</template>

<script>
import { debounce } from 'debounce';

let templates = {
  enums: `
enum Direction {
    Up = 1,
    Down,
    Left,
    Right,
}
  `,
  interfaces: `
interface LabelledValue {
    label: string;
}

function printLabel(labelledObj: LabelledValue) {
    console.log(labelledObj.label);
}

let myObj = {size: 10, label: "Size 10 Object"};
printLabel(myObj);
  `,
  classes: `
class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    greet() {
        return "Hello, " + this.greeting;
    }
}

let greeter = new Greeter("world");
  `,
  symbols: `
let sym1 = Symbol();

let sym2 = Symbol("key"); // optional string key
  `,
  functionTypes: `
function add(x: number, y: number): number {
    return x + y;
}

let myAdd = function(x: number, y: number): number { return x + y; };
  `,
  forOf: `
let someArray = [1, "string", false];

for (let entry of someArray) {
    console.log(entry); // 1, "string", false
}
  `,
  unionTypes: `
interface Bird {
    fly();
    layEggs();
}

interface Fish {
    swim();
    layEggs();
}

function getSmallPet(): Fish | Bird {
    // ...
}

let pet = getSmallPet();
pet.layEggs(); // okay
pet.swim();    // errors
  `,
  asyncAwait: `
async function main() {
  await wait();
}

main();
  `,
};

export default {
  name: 'InputViewer',
  data: function() {
    return {
      preset: '',
      code: '',
    };
  },
  props: [
    'writtenCode',
  ],
  watch: {
    preset: function(value) {
      if (value === '') {
        this.code = '';
      }
      if (value in templates) {
        this.code = templates[value].trim();
      }
    },
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
.header-group {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
h2 {
  margin: 0;
  font-size: 1rem;
  line-height: 1.5;
  text-align: left;
}
.preset {
  min-width: 7rem;
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
