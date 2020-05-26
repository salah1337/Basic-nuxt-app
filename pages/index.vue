<template>
  <div>
    <div class="content">
        <h1 class="title">Movie Finder</h1>
        <input v-model="title" disabled class="input" type="text">
        <nuxt-link :to="`/movies`">
          <a class="btn">Find</a>
        </nuxt-link>
    </div>
  </div>
</template>

<script>


export default {
  data() {
    return{
      title:''
    }
  }, 
  methods: {
    findMovie: function() {

    }
  }
}
</script>

<style lang="scss">
@import "~/assets/scss/movies/main.scss";
</style>
