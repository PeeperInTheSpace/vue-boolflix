<template>
  <section>
    <img :src="baseUrl+arrayElement.poster_path" alt="cover">
  </section>
</template>

<script>
export default {
  name: "CardSection",
  props: ["arrayElement"],
  data () {
    return {
      baseUrl: "https://image.tmdb.org/t/p/w300"
    }
  }
}
</script>

<style lang="scss" scoped>

  * {
    color: white;
  }

</style>