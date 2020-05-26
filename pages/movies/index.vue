<template>
   <div class="content">
        <div class="search">
            <input v-model="title" class="input" type="text">
            <a class="btn">Find</a>
        </div>
        <div class="list">
                <div class="movie" v-for="movie in movies" :key="movie.imdbID" >
                <nuxt-link :to="`/movies/${movie.imdbID}`" >
                <img v-if="movie.Poster !== 'N/A'" :src="`${ movie.Poster }`" alt="">
                <img v-else src="~/assets/placeholder.jpg" alt="">
                <div>
                    <h3>{{movie.Title}}</h3>
                    <h5>{{movie.Year}}</h5>
                </div>
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
@import "~/assets/scss/movies/list.scss";
</style>
