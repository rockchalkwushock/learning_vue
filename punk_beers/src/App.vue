<template>
  <div id="app">
    <section>
    <h1>🍺 Make yourself some Punk Beers 🍻</h1>
    <div v-if="beers.length === 0" class="loading">Loading...</div>
    <div v-for="beer in beers" class="beer-contain">
      <div class="beer-img">
        <img :src="beer.img" height="350" />
      </div>
      <div class="beer-info">
        <h2>{{ beer.name }}</h2>
        <p class="bright">{{ beer.tagline }}</p>
        <p><span class="bright">Description:</span> {{ beer.desc }}</p>
        <p><span class="bright">Tips:</span> {{ beer.tips }}</p>
        <h3 class="bright">Food Pairings</h3>
        <ul>
          <li v-for="item in beer.food">
            {{ item }}
          </li>
        </ul>
      </div>
    </div>
  </section>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  data() {
    return {
      bottom: false,
      beers: []
    }
  },
  watch: {
    bottom(bottom) {
      // When we reach the bottom run the api call for more beers.
      if (bottom) {
        this.addBeer()
      }
    }
  },
  created() {
    window.addEventListener('scroll', () => {
      this.bottom = this.bottomVisible()
    })
    this.addBeer()
  },
  methods: {
    bottomVisible() {
      const scrollY = window.scrollY
      const visible = document.documentElement.clientHeight
      const pageHeight = document.documentElement.scrollHeight
      const bottomOfPage = visible + scrollY >= pageHeight
      return bottomOfPage || pageHeight < visible
    },
    addBeer() {
      axios.get('https://api.punkapi.com/v2/beers/random').then(response => {
        let api = response.data[0]
        let apiInfo = {
          name: api.name,
          desc: api.description,
          img: api.image_url,
          tips: api.brewers_tips,
          tagline: api.tagline,
          food: api.food_pairing
        }
        this.beers.push(apiInfo)
        if (this.bottomVisible()) {
          this.addBeer()
        }
      })
    }
  }
}
</script>

<style>
body {
  font-family: 'Archivo Narrow', sans-serif;
  background: #25859a;
}

h1,
h2,
h3,
h4 {
  font-family: 'Fjalla One', sans-serif;
}

h1 {
  margin-top: 40px;
  color: white;
  text-align: center;
}

.loading {
  color: white;
  text-align: center;
  font-size: 20px;
}

.display,
#app,
.beer-contain,
.beer-img {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  -ms-flex-line-pack: center;
  align-content: center;
}

#app {
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
}

.beer-contain {
  width: 50%;
  margin: 20px 24%;
  -webkit-box-shadow: 0 2px 3px 1px rgba(30, 0, 0, 0.1);
  box-shadow: 0 2px 3px 1px rgba(30, 0, 0, 0.1);
}

.beer-img {
  padding: 30px;
  background: #ff6542;
  border: 1px solid #88498f;
  border-right: 1px solid #f44822;
}

.beer-info {
  background: #564154;
  color: white;
  padding: 30px;
  border: 1px solid #88498f;
}
.beer-info .bright {
  color: #fcd7cf;
  font-family: 'Contrail One', sans-serif;
}

h3 {
  margin-bottom: 5px;
}

ul {
  margin-top: 5px;
}
</style>
