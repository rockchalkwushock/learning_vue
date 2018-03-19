# My Notes

## Methods

Are bound to the Vue instance, they are incredibly useful for functions you would like to access in directives.

* Runs whenever an update occurs.
* Not cached.
* Typically invoked from v-on/@, but flexible.
* Getter/Setter.

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

## Computed

Computed properties are calculations that will be cached and will only updated when needed.

Highly performant but use with understanding.

A different view of the same data. Think of `.map()` copying and returning a new view of the same data.

* Runs only when a dependency has changed.
* Cached
* Should be used as a property, in place of data.
* By default getter only, but you can define a setter.

```javascript
new Vue({
  el: '#app',
  data() {
    return {
      userData: ''
    }
  },
  computed: {
    greeting() {
      return `You are a monster, ${this.userData}!`
    }
  }
})
```

```html
<div>
  <h3>Your Name: <input v-model.lazy="userData" /></h3>
  <h2 v-if="userData">Initial entry: {{ userData }}</h2>
  <h2 v-if="userData">Computed value: {{ greeting }}</h2>
</div>
```

## Watchers

Good for asynchronous updates, and updates/transitions with data changes.

### What is Reactive?

Reactive programming is programming with asynchronous data streams.

A **stream** is a sequence of ongoing events ordered in time that offer some hooks with which to observe it.

When we use reactive premises for building applications, this means it's very easy to update state in reaction to events.

> Vue cannot detect property addition or deletion so we create the `data` object to keep track.

1.  Each component has a watcher instance.
2.  The properties touched by the watcher during the render are registered as dependencies.
3.  When the setter is triggered, it lets the watcher know, and causes the component to re-render.

```javascript
new Vue({
  el: '#app',
  data() {
    return {
      counter: 0
    }
  },
  watch: {
    // NOTE:
    // This has to match the data property we are watching!
    counter() {
      console.log('The counter has changed!')
    }
  }
})
```

```html
<div id="app">
  <input type="number" v-model.number="counter"></input>
</div>
```

I have access to the new and old value with watchers

```javascript
watch: {
  watchedProperty(value, oldValue) {
    // ...
  }
}
```

Can also go deep!

```javascript
watch: {
  watchedProperty: {
    deep: true,
    nestedWatchedProperty(value, oldValue) {
      // ...
    }
  }
}
```

## Templates

Vue.js uses HTML-based template syntax to bind the Vue instance to the DOM, very useful for components.

Templates are optional, you can also write render functions with option JSX support.

## Components

A collection fo elements that are encapsulated into a group that can be accessed through one single element.

```javascript
Vue.component('child', {
  template: `<div>hello vue</div>`
})

new Vue({
  el: '#app'
})
```

```html
<div id="app">
  <child></child>
</div>
```

### With props

```javascript
Vue.component('child', {
  props: ['text'],
  template: `<div>Hello {{ text }}!</div>`
})

new Vue({
  el: '#app',
  data() {
    return {
      message: 'Vue'
    }
  }
})
```

```html
<div id="app">
  <child :text="message"></child>
</div>
```

### With props validation

```javascript
Vue.component('child', {
  props: {
    text: [String, Number],
    otherText: {
      type: String,
      required: true,
      default: 'Hello Vue!'
    },
    someOtherText: {
      // NOTE
      // Objects & Arrays must be returned from functions.
      type: Object,
      default: function() {
        return { message: 'Pizza!' }
      }
    }
  },
  template: `<div>Hello {{ text }}!</div>`
})

new Vue({
  el: '#app',
  data() {
    return {
      message: 'Vue'
    }
  }
})
```

Not using the state of the parent `<child count="1"></child>` vs using the state of the parent `<child :count="count"></child>`. We use `v-bind` or `:` to dynamically bind props to data on the parent.

Each component has isolated scope so we must return data as a function.
