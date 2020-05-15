<template>
<div>
    <b-carousel
    id="carousel-fade"
    style="text-shadow: 0px 0px 2px #000"
    fade
    :interval="3000"
    indicators
    img-width="1980"
    img-height="790"
  >
      <b-carousel-slide>
        <template v-slot:img>
          <img
            class="d-block img-fluid w-100"
            width="1980"
            height="790"
            src="../assets/hero-img2.png"
            alt="image slot"
          >
        </template>
      </b-carousel-slide>

      <b-carousel-slide>
        <template v-slot:img>
          <img
            class="d-block img-fluid w-100"
            width="1980"
            height="790"
            src="../assets/hero-img.jpg"
            alt="image slot"
          >
        </template>
      </b-carousel-slide>
  </b-carousel>

<!-- The App Section -->
<div class="container">
  <div class="row">
    <div class="column-66">
      <h1 class="xlarge-font"><b>Meal Website</b></h1>
      <h1 class="large-font" style="color:MediumSeaGreen;"><b>What it is?</b></h1>
      <p><span style="font-size:36px">Find meals around the world here.</span> This website contain almost all meals around the world where you can find it easy and also learn how to make it.</p>
      <router-link to="/search" class="button">Start Searching</router-link>
    </div>
    <div class="column-33">
        <img src="../assets/meal2.png" width="335" height="471" >
    </div>
  </div>
</div>

<!-- Clarity Section -->
<div class="container" style="background-color:#f1f1f1">
  <div v-for="result in results" :key="result.idMeal" style="text-align: center;">
    <div class="row">
      <div class="column-33">
            <img class="card" :src="result.strMealThumb" width="335" height="471">
      </div>
      <div class="column-66">
        <h1 class="xlarge-font"><b>{{ result.strMeal }}</b></h1>
        <h1 class="large-font" style="color:red;"><b>Origin : {{result.strArea}}</b></h1>
        <p><span style="font-size:24px">A revolution in resolution.</span> Sharp and clear photos with the world's best photo engine, incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquipex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.</p>
        <router-link :to="{ name: 'Detail', params: { id: result.idMeal } }">
          <button class="button" style="background-color:red">Read More</button>
        </router-link>
      </div>
    </div>
  </div>
</div>

<!-- The App Section -->
<div class="container">
  <div class="row">
    <div class="column-66">
      <h1 class="xlarge-font"><b>Search A Lot More</b></h1>
      <h1 class="large-font" style="color:MediumSeaGreen;"><b>How?</b></h1>
      <p>you can search more meals using our search system, you can even search meals by filtering the origin of the cuisine, the category, and the ingredient that it needs.<span style="font-size:36px"> Starts Now.</span></p>
      <router-link to="/filter" class="button">Search by filter</router-link>
    </div>
    <div class="column-33">
        <img src="../assets/meal.png" width="335" height="471" >
    </div>
  </div>
</div>

  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
      results: []
    }
  },
  mounted () {
    axios.get('https://www.themealdb.com/api/json/v1/1/random.php').then(response => {
      console.log(response.data.meals)
      this.results = response.data.meals
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  box-sizing:border-box;
}

body {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

.container {
  padding: 64px;
}

.row:after {
  content: "";
  display: table;
  clear: both
}

.column-66 {
  float: left;
  width: 66.66666%;
  padding: 20px;
}

.column-33 {
  float: left;
  width: 33.33333%;
  padding: 20px;
}

.large-font {
  font-size: 48px;
}

.xlarge-font {
  font-size: 64px
}

.button {
  border: none;
  color: white;
  padding: 14px 28px;
  font-size: 16px;
  cursor: pointer;
  background-color: #4CAF50;
}

img {
  display: block;
  height: auto;
  max-width: 100%;
}

@media screen and (max-width: 1000px) {
  .column-66,
  .column-33 {
    width: 100%;
    text-align: center;
  }
  img {
    margin: auto;
  }
}
</style>
