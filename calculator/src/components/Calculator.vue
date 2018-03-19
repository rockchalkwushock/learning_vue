<template>
  <div class="calculator">
    <div class="row">
      <input v-model.number="num1" type="number">
      <span>+</span>
      <input v-model.number="num2" type="number">
      <span>=</span>
      <span>{{ num1 + num2 }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Calculator',
  data() {
    return {
      num1: 0,
      num2: 0
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.row {
  margin: 50px;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  font-family: 'Work Sans', sans-serif;
}

input,
span {
  padding: 10px;
  font-size: 30px;
  font-family: 'Work Sans', sans-serif;
}

input {
  width: 50px;
}

span {
  width: 20px;
}
</style>
