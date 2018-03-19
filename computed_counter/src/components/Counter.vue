<template>
  <div class="counter">
    <p>counter: {{ counter }}</p>
    <p>counter computed: {{ countupComp }}</p>
    <button @click="countup">Increase</button>
  </div>
</template>

<script>
export default {
  name: 'Counter',
  data() {
    return {
      counter: 0
    }
  },
  methods: {
    countup() {
      this.counter++
    }
  },
  computed: {
    countupComp() {
      return this.counter + 1
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
