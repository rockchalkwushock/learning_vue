<template>
  <div class="place">
    <img :src="img" width="235" height="300"/>
    <slot></slot>
    <p>{{ desc }}</p>
  </div>
</template>

<script>
export default {
  name: 'Place',
  props: ['desc', 'img']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.place {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
  width: 280px;
  height: 320px;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  background: white;
  border: 1px solid #ddd;
  padding: 20px 20px;
  margin: 10px;
}
.place h2 {
  margin: 0;
  text-align: center;
}
.place img {
  margin: 10px;
  -ms-flex-item-align: center;
  align-self: center;
}
</style>
