<template>
  <MyTable msg="Welcome to Your Vue.js + TypeScript App"/>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import MyTable from './components/MyTable.vue';
let a=1
export default defineComponent({
  name: 'App',
  components: {
    MyTable
  }
});
</script>

<style>
#app {
  font-family: "Microsoft YaHei";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
