<template>
  <div class="container mt-5">
      <!-- <h1>This is a search page</h1> -->
    <div class="row">
        <div class="col-md-3 mb-3" v-for="result in results" :key="result.idMeal" style="text-align: center;">
            <div class="card" style="width: 15rem; height: 100%;">
              <router-link :to="{ name: 'Detail', params: { id: result.idMeal } }">
              <img class="card-img-top" :src="result.strMealThumb">
              <div class="card-body">
                <h5 class="card-title">{{ result.strMeal }}</h5>
              </div>
              </router-link>
              <button class="btn-danger" style="border-radius: 8%" @click="addFav(result.idMeal,result.strMealThumb,result.strMeal,result.strCategory)">Save</button>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
const STORAGE_KEY = 'DaftarFavorit'
export default {
  name: 'Foods',
  data () {
    return {
      results: [],
      fav: []
    }
  },
  mounted () {
    axios.get('https://www.themealdb.com/api/json/v1/1/filter.php?', {
      params: {
        a: this.$route.params.name
      }
    })
      .then(response => {
        this.results = response.data.meals
      })
  },
  methods: {
    addFav (favId, favPict, favName, favCategory) {
      this.fav.push({ id: favId, picture: favPict, name: favName, category: favCategory })
      localStorage.setItem(STORAGE_KEY, JSON.stringify(this.fav))
      this.$toast.success('Added to favorites !', {
        theme: 'bubble',
        position: 'top-center',
        duration: '1500'
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
