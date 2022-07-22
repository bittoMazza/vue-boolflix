<template>
    <div v-show="searchedFilms.length != 0" class="py-5 scroll-style">
        <h2 class="text-white text-start">FILM</h2>
        <div class="scrollmenu">
            <Card class="d-inline-block"  v-for="film in searchedFilms" :key="film.id" 
            :listItem="film"
            />
        </div>
    </div>
</template>

<script>
import Card from "./Card.vue"
export default {
     props:{
        searchedFilms:Array,
    },
    components:{
        Card,
    },
}
</script>

<style lang="scss">
@import "../styles/variables.scss";

</style>