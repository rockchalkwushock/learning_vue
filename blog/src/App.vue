<template>
  <div id="app">
    <img src="./assets/logo.png">
    <Blog/>
  </div>
</template>

<script>
import Blog from './components/Blog'

export default {
  name: 'App',
  components: {
    Blog
  }
}
</script>

<style>
#app {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  font-family: 'Work Sans', sans-serif;
}
</style>
