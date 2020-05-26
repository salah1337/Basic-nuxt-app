<template>
  <div>
    <navBar />
    <nuxt />
  </div>
</template>
<script>
import navBar from '~/components/navBar.vue'

export default {
  components: {
    navBar
  }
}
</script>
<style>
@import "~/assets/scss/main.scss";
</style>
