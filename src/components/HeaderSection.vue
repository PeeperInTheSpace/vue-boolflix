<template>
  <header>
    <div class="fl-logobox h-100 px-5 d-flex align-items-center justify-content-between">
        <img src="../assets/img/logo.png" alt="logo">
        <div class="input-group w-25">
            <input type="text" class="form-control" placeholder="Cerca Film o Serie TV" v-model="searchText">
            <button class="btn btn-danger" type="button" @click="$emit('sendInputText', searchText)">Cerca</button>
        </div>
        <button type="button" class="btn btn-danger">Accedi</button>
    </div>

  </header>
</template>

<script>
export default {
    data () {
        return {
            searchText: ""
        }
    }
}
</script>

<style lang="scss" scoped>

    header {
        height: 10vh;
        min-width: 100%;
        background-color: transparent;
        position: fixed;

        .fl-logobox {
            background-color: transparent;

            img {
            height: 100px;;
            }

            button {
                height: 50px;
                width: 100px;
                font-size: 20px;
            }

        }

    }

</style>