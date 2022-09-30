<template>
  <section>
    <div v-if="!this.active" @click="changeStatus()" class="poster">
      <img v-if="arrayElement.poster_path" :src="baseUrl+arrayElement.poster_path" :alt="arrayElement.title ? arrayElement.title : arrayElement.name" class="rounded-3">
      <img v-else src="../assets/img/no_poster.jpg" alt="Poster-not-available" class="fl-noposter rounded-3">
    </div>
    <div v-else @click="changeStatus()" class="informations rounded-3">
      <div>
        <!-- TITOLO -->
        <h3>Titolo:</h3>
        {{ arrayElement.title ? arrayElement.title : arrayElement.name }}
      </div>
      <!-- TITOLO ORIGINALE -->
      <div>
        <h3>Titolo Originale:</h3>
        {{
          arrayElement.original_title ? arrayElement.original_title : arrayElement.original_name
        }}
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
        <span class="gold" v-for="(item, index) in this.vote" :key="'A' + index"
          ><i class="fas fa-star"></i
        ></span>
        <span v-for="(item, index) in this.voidStar" :key="'B' + index"
          ><i class="fas fa-star"></i
        ></span>
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
      active: false
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
    border: 1px white solid
  }

</style>