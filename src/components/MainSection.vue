<template>
    <main>
        <CardsSection />
    </main>
</template>

<script>
import CardsSection from './CardsSection.vue';
export default {
    components: { CardsSection }
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
    }


</style>