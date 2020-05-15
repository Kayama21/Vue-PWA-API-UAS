<template>
  <div class="container">
  <div class="row">
    <div class="column-66">
      <h1 class="xlarge-font"><b>Kharisma Arya</b></h1>
      <p>Website ini dibuat untuk para penikmat kuliner di seluruh dunia, merangkum banyak sekali makanan dari berbagai negara beserta cara pembuatannya. Website ini dibuat dengan mengimplementasikan API dari <a href="http://www.themealdb.com">The Meal DB</a></p>
    </div>
    <div class="column-33">
        <img src="../assets/3x4.jpeg" width="200px" style="border-radius: 2%">
    </div>
  </div>
</div>
</template>

<style scoped>
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
