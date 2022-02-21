
<script setup lang="ts">
import Editor from "../components/editor/editor.vue";
import {ref} from 'vue'
let msg = ref("");
</script>

<template>
  <div>{{msg}}</div>
  <img alt="Vue logo" src="./assets/logo.png" />
  <Editor v-model="msg"></Editor>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
