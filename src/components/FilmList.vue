<template>
    <div class="py-5 scroll-style">
        <h2 class="text-white text-start">FILM</h2>
        <div class="d-flex flex-wrap">
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

<style lang="scss" scoped>
@import "../styles/variables.scss";

</style>