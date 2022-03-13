<template>
  <div id="app">
    <Title />
    <Table />
  </div>
</template>

<script>
import Title from './components/BaseTitle.vue'
import Table from './components/BaseTable.vue'

export default {
  name: 'App',
  components: {
    Title,
    Table
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
  padding: 20px;
}
</style>
