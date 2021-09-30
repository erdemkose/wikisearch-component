<template>
  <div id="app">
    <WikiSearchWidget/>
  </div>
</template>

<script>
import WikiSearchWidget from "@/components/WikiSearchWidget";

export default {
  name: 'App',
  components: {
    WikiSearchWidget,
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  max-width: 640px;
}
</style>
