# My Notes

## Methods

Are bound to the Vue instance, they are incredibly useful for functions you would like to access in directives.

```javascript
new Vue({
  el: '#app',
  data() {
    return {
      counter: 0,
      x: 0
    }
  },
  methods: {
    // Can't use => here
    decrement() {
      // Can use => here
      // binding of this issue.
      this.counter--
    },
    increment() {
      this.counter++
    },
    // e or event is available to me thanks to Vue.
    xCoordinate(e) {
      this.x = e.clientX
    }
  }
})
```

```html
<button @click="increment">Add</button>
  {{ counter }}
<button @click="decrement">Subtract</button>
```
