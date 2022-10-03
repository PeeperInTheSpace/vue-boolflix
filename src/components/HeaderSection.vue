<template>
  <header>
    <div class="fl-logobox px-5 d-flex align-items-center justify-content-between">
        <img src="../assets/img/logo.png" alt="logo">
        <div class="input-group w-25">
            <input type="text" class="form-control fs-5" placeholder="Cerca Film o Serie TV" v-model="searchText" @keyup.enter="$emit('sendInputText', searchText)">
            <button class="btn btn-danger" type="button" @click="$emit('sendInputText', searchText)">Cerca</button>
        </div>
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
        padding-top: 2vh;
        min-width: 100%;
        background-color: transparent;
        position: fixed;

        .fl-logobox {
            background-color: transparent;

            img {
            height: 80px;

                &:hover {
                    transition: all 1s;
                    filter: drop-shadow(0 0 1.5rem red);
                }
            }

            button {
                height: 50px;
                width: 100px;
                font-size: 20px;
            }

            input {

            }

        }

    }

</style>