<template>
  <div class="comments">
    <ul>
    <li v-for="comment in comments">{{ comment }}</li>
  </ul>
  <input v-model="newComment" @keyup.enter="addComment" placeholder="Add a comment" type="text">
  </div>
</template>

<script>
export default {
  name: 'Comments',
  data() {
    // Make sure you return!!!
    return {
      newComment: '',
      comments: ['Looks great Julianne', 'I love the sea', 'Where are you at?']
    }
  },
  methods: {
    addComment() {
      this.comments.push(this.newComment)
      this.newComment = ''
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
