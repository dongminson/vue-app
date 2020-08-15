<template>
  <MainForm />
</template>

<script>
import MainForm from './components/MainForm.vue'
import Vue from 'vue'
import VueMaterial from 'vue-material'
import 'vue-material/dist/vue-material.min.css'
import 'vue-material/dist/theme/default.css'

Vue.use(VueMaterial)
export default {
  name: 'App',
  components: {
    MainForm
  }
}
</script>

<style>
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-image: linear-gradient(#673ab7, #512da8);
  height: 100vh;
  width: 100vw;
  flex-wrap: wrap;

}
</style>
