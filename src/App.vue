<template>
  <div id="app">
    <HeaderSection @sendInputText="saveInputText" />
    <MainSection :movies="myMoviesArray" :series="mySeriesArray" />
  </div>
</template>

<script>
import HeaderSection from './components/HeaderSection.vue';
import MainSection from './components/MainSection.vue';
import axios from "axios";

export default {
  name: 'App',
  components: {
    HeaderSection,
    MainSection
},

  data () {
    return {
      textInput: "",
      myKey: "bc3c3715a5f54bee697a61d627f598a4",
      myMoviesArray: [],
      mySeriesArray: [],
    }
  },

  methods: {

    saveInputText (value) {

      this.textInput = value
      this.callApiMovies ()
      this.callApiSeries ()

    },

    callApiMovies () {

      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.myKey}&query=${this.textInput}`)
      .then((response) => {

        if (this.textInput.length > 0) {

          this.myMoviesArray = response.data.results

        }

      })

    },

    callApiSeries () {

      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.myKey}&query=${this.textInput}`)
      .then((response) => {
        console.log(response)
        if (this.textInput.length > 0) {

        this.mySeriesArray = response.data.results
        
        }

      })

    }

  }

}
</script>

<style lang="scss">

@import "./style/common.scss"; 

</style>
