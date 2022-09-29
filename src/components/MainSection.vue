<template>
    <main>
        <section class="d-flex container justify-content-center flex-wrap mt-5 gap-5">
            <CardsSection :arrayElement="film" v-for="film in movies" :key="film.id"/>
            <CardsSection :arrayElement="serie" v-for="serie in series" :key="serie.id"/>
        </section>
    </main>
</template>

<script>
import CardsSection from './CardsSection.vue';
export default {
    components: { CardsSection },

    props: {
        movies:Array,
        series:Array,
    }
}
</script>

<style lang="scss" scoped>

    main {
        height: 100vh;
        background-color: black;
        padding-top: 10vh;
        background-image: url(../assets/img/Background.jpg);
        background-repeat: no-repeat;
        background-size: cover;
        overflow-y: auto;
    }


</style>