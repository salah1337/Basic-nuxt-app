<template>
  <div class="container">
      <div>
        <h1>
          The movie library
        </h1>
        <nuxt-link :to="'/movies'">
          <h5>
            Go to movies list
          </h5>
        </nuxt-link>
        <nuxt-link :to="'/movies/random'">
          <h5>
            Get random movie
          </h5>
        </nuxt-link>
      </div>
  </div>
</template>

<script>

export default {
  async asyncData({ $axios }){
    let res = await $axios.get('/?apikey=2d879e3a&s=hobbit')
    let movies = res.data.Search
    let count = res.data.totalResults
    return {
      movies, 
      count
    }
  },
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;

}
</style>
