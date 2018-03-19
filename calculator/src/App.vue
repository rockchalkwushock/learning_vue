<template>
  <div id="app">
    <img src="./assets/logo.png">
    <Calculator/>
    <Tacos />
  </div>
</template>

<script>
import Calculator from './components/Calculator'
import Tacos from './components/Tacos'

export default {
  name: 'App',
  components: {
    Calculator,
    Tacos
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
