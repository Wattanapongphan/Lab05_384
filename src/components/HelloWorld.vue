<script setup>
import { ref } from 'vue';
import { reactive } from 'vue';

defineProps({
  msg: String,
})

const x = ref(0);
const y = ref(0);
const answer = ref(0);

const count = ref(0);
let name = ref('Wattanapongphan');
const lightstatus = ref(false)

const styleObject = reactive({
  color: 'red',
  fontSize: '13px'
})

function upsize(){
  count.value++;
  console.log(styleObject.fontSize.slice(0,-2));
  styleObject.fontSize = `${20 + count.value}px`;
}

function turnon(){
lightstatus.value = !lightstatus.value;
}

function add(){
answer.value = x.value+y.value;
}
</script>

<template>
  <h1>{{ msg }}</h1>
  <h2 :style="styleObject" >{{ name }}</h2>

  <form>
    ชื่อ <input type="text" v-model="name"><br>
    บวกเลข
    <input type="number" v-model="x">+<input type="number" v-model="y"><br>
    <button @click="add()">คำตอบ {{ answer }}</button>
    
  </form>

  <div class="card">
    <button @click="turnon">on/off</button>{{ lightstatus }}

    <button type="button"  @click="upsize">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
