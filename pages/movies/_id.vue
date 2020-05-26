<template>
 <div class="content">
        <img v-if="movie.Poster !== 'N/A'" :src="`${ movie.Poster }`" alt="">
        <img v-else src="~/assets/placeholder.jpg" alt="">
        <div class="info">
            <h3 class="title">{{movie.Title}}  {{movie.Year}}</h3>
            <h4 class="subtitle">{{movie.Runtime}} {{movie.imdbRating}}</h4>
            <div class="description">
                {{movie.Plot}}            
            </div>
            <div class="actors">{{movie.Actors}}</div>
            <div class="origin">{{movie.Language}} {{movie.Country}}</div>
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