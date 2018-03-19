<template>
  <div class="tacos">
    <div class="row second">
      <select v-model="name">
        <option>Carne Asada</option>
        <option>Pollo</option>
        <option>Bean</option>
        <option>Al Pastor</option>
      </select>
      <p v-if="name">My favorite taco is {{ name }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Tacos',
  data() {
    return {
      name: ''
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
.second {
  font-size: 18px;
}
.second p {
  margin-left: 20px;
}
</style>
