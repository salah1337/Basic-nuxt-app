<template>
  <div class="container">
      <div class="titleBar">
        <h1>
          The movie library
        </h1>
      </div>
      <div class="searchBar">
        <div class="input">
        <label for="">Title</label>
        <input type="text" v-model='title'>
        </div>
        <div class="input">
        <label for="">Year</label>
        <input type="number" v-model='year'>
        </div>
        <button @click="getMovies()">Search</button>
        <h4 v-if="response == 'True'">
            {{ count }} Results
        </h4>
        <h4 v-else>
            Error! {{ error }}
        </h4>
      </div>
    <div class="movieList">
        <div class="movie" v-for="movie in movies" :key="movie.imdbID">
            <nuxt-link class="link" :to="`/movies/${movie.imdbID}`">
            <img v-if="movie.Poster !== 'N/A'" :src="`${ movie.Poster }`" alt="">
            <img v-else src="~/assets/placeholder.jpg" alt="">
            <h5>
                {{ movie.Title }}
                <p>
                {{ movie.Year }}
                </p>
            </h5>
            </nuxt-link>
        </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return{
            title:'hobbit',
            year:'',
            movies:[],
            count:0,
            response:'', 
            error:''
        }
    },
    async created(){
        this.getMovies()
    },
    methods: {
        getMovies: async function() {
            let res = await axios.get(`https://www.omdbapi.com/?apikey=2d879e3a&s=${this.title}&y=${this.year}`)
            this.movies = res.data.Search
            this.count = res.data.totalResults
            this.response = res.data.Response
            this.error = res.data.Error
        }
    }
}
</script>

<style lang='scss'>
@import "~/assets/scss/movies/main.scss";
</style>
