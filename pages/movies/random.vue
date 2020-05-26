<template>
  <div class="container">
      <div>
        <nuxt-link :to="'/movies'">
          <h4>
            Back to all
          </h4>
        </nuxt-link>
      </div>
      <!-- <div style="display=flex">
          <h5>
            {{ movie.Title }}
          </h5>
        <p>
          {{ movie.Year }}
        </p>
        <br/>
      </div> -->
  </div>
</template>

<script>

export default {
    data(){
        return {
            rand: this.randomInt(20)
        }
    },
//   async asyncData({ $axios }){
//     let res = await $axios.get(`/?apikey=2d879e3a&i=${ params.id }`)
//     let movie = res.data
//     return {
//       movie
//     }
//   },
  methods:{
    randomInt: function (max) {
        return Math.floor(Math.random() * Math.floor(max));
    },
  }
}
</script>

