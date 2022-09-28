<template>
  <div id="app">
    <HeaderSection @sendInputText="saveInputText" />
    <MainSection />
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
      myKey: "bc3c3715a5f54bee697a61d627f598a4"
    }
  },

  methods: {

    saveInputText (value) {

      this.textInput = value
      this.callApiMovies ()

    },

    callApiMovies () {

      axios.get(`https://api.themoviedb.org/3/movie?api_key=${this.myKey}&query=${this.textInput}`)
      .then((response) => {
        console.log(response)
      })

    }

  }

}
</script>

<style lang="scss">

@import "./style/common.scss"; 

</style>
