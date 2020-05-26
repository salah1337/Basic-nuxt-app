<template>
  <div class="container">
      <div>
        <nuxt-link :to="'/movies'">
          <h4>
            Back to all
          </h4>
        </nuxt-link>
      </div>
      <div class="movie">
        <div>
        <img v-if="movie.Poster !== 'N/A'" :src="`${ movie.Poster }`" alt="">
        <img v-else src="~/assets/placeholder.jpg" alt="">
        </div>
        <div>
          <h5>
          {{ movie.Title }} <span class="year"> {{ movie.Year }} </span>
          <p class="runtime"> {{ movie.Runtime }} </p>
          </h5>
          <p>
          <span class="label"> Description </span> <br/> <span class="description"> {{ movie.Plot }} </span>
          </p>
          <p class="imdbScore">IMDB: {{ movie.imdbRating }} </p>
        </div>
      </div>
  </div>
</template>

<script>

export default {
  async asyncData({ $axios, params }){
    let res = await $axios.get(`/?apikey=2d879e3a&i=${ params.id }`)
    let movie = res.data
    return {
      movie
    }
  },
}
</script>

<style lang="scss">
@import "~/assets/scss/movies/show.scss";
</style>