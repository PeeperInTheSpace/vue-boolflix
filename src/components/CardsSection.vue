<template>
  <section>
    <div class="poster">
      <img v-if="arrayElement.poster_path" :src="baseUrl+arrayElement.poster_path" :alt="arrayElement.title ? arrayElement.title : arrayElement.name">
      <img v-else src="../assets/img/no_poster.jpg" alt="Poster-not-available" class="fl-noposter">
    </div>
    <div class="informations">
      <div>
        <h3>Titolo:</h3>
        {{ arrayElement.title ? arrayElement.original_title : arrayElement.original_name }}
      </div>
      <div>

      </div>

    </div>
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

  .fl-noposter {
    height: 450px;
    width: 300px;
  }

  .poster {
    height: 450px;
    width: 300px;
  }

  .informations {
    height: 450px;
    width: 300px;
    // display: none;
    background-color: white;
  }

  .poster:hover .informations {
    display: block;
  }

  .poster:hover {
    display: none;
  }

</style>