<template>
  <div id="app">
    <DeleteItem />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import DeleteItem from "./components/DeleteItem.vue";

export default {
  name: 'App',
  components: {
    DeleteItem,
}
}
</script>

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
