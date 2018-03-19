<template>
  <div class="form">
    <form @submit.prevent="submitForm">
      <div>
        <label for="name">Name:</label><br>
        <input v-model="name" id="name" required type="text" />
      </div>
      <div>
        <label for="email">Email:</label><br>
        <input v-model="email" id="email" required type="email" />
      </div>
      <div>
        <label for="caps">HOW DO I TURN OFF CAPS LOCK:</label><br>
        <textarea v-model="caps" id="caps" required></textarea>
      </div>
      <button :class="[name ? activeClass : '']" type="submit">Submit</button>
      <div>
        <h3>Response from server:</h3>
        <pre>{{ response }}</pre>
      </div>
    </form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Form',
  data() {
    return {
      userID: 1,
      name: '',
      email: '',
      caps: '',
      response: '',
      activeClass: 'active'
    }
  },
  methods: {
    submitForm() {
      axios
        .post('//jsonplaceholder.typicode.com/posts', {
          userID: this.userID,
          name: this.name,
          email: this.email,
          caps: this.caps
        })
        .then(response => {
          this.response = JSON.stringify(response, null, 2)
        })
        .catch(error => {
          this.response = `Error: ${error.response.status}`
        })
    }
  }
}
</script>
