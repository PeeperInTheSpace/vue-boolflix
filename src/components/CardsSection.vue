<template>
  <section>
    <div v-if="!this.active" @click="changeStatus()" class="poster">
      <img v-if="arrayElement.poster_path" :src="baseUrl+arrayElement.poster_path" :alt="arrayElement.title ? arrayElement.title : arrayElement.name" class="rounded-3 h-100 w-100">
      <img v-else src="../assets/img/no_poster.jpg" alt="Poster-not-available" class="fl-noposter rounded-3">
    </div>
    <div v-else @click="changeStatus()" class="informations rounded-3 d-flex flex-column p-3">
      <div>
        <!-- TITOLO -->
        <h3>Titolo:</h3>
        <h5>
          {{ arrayElement.title ? arrayElement.title : arrayElement.name }}
        </h5>
      </div>
      <!-- TITOLO ORIGINALE -->
      <div>
        <h3>Titolo Originale:</h3>
        <h5>
        {{
          arrayElement.original_title ? arrayElement.original_title : arrayElement.original_name
        }}
        </h5>
      </div>
      <!-- LINGUA -->
      <div>
        <div v-if="arrayElement.original_language === 'it'">
          <h4>Lingua:</h4>
          <span :class="`fi fi-it`"></span>
        </div>
        <div v-else-if="arrayElement.original_language === 'es'">
          <h4>Lingua:</h4>
          <span :class="`fi fi-es`"></span>
        </div>
        <div v-else-if="arrayElement.original_language === 'en'">
          <h4>Lingua:</h4>
          <span :class="`fi fi-gb`"></span>
        </div>
        <div v-else-if="arrayElement.original_language === 'ja'">
          <h4>Lingua:</h4>
          <span :class="`fi fi-jp`"></span>
        </div>
        <div v-else-if="arrayElement.original_language === 'fr'">
          <h4>Lingua:</h4>
          <span :class="`fi fi-fr`"></span>
        </div>
        <div v-else>
          <h4>Lingua:</h4>
          {{ arrayElement.original_language }}
        </div>
      </div>
      <!-- VOTO -->
      <div>
        <h5>Voto:</h5>
          <i class="fas fa-star gold" v-for="(item, index) in this.vote" :key="'A' + index"></i>
          <i class="fas fa-star" v-for="(item, index) in this.voidStar" :key="'B' + index"></i>
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
      baseUrl: "https://image.tmdb.org/t/p/w300",
      active: false,
      vote: Math.ceil(this.arrayElement.vote_average / 2),
      voidStar: 5 - Math.ceil(this.arrayElement.vote_average / 2),
    }
  },

  methods: {

    changeStatus() {

      this.active = !this.active

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
    background-color: rgba(0, 0, 0, 0.525);
    box-shadow: 1px 4px 28px 10px #FFFFFF;
  }

  
  .gold {
    color: gold;
  }

</style>