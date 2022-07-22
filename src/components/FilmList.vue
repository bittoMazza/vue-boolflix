<template>
    <div class="py-3">
        <h2 class="text-white text-center">Film</h2>
        <div class="d-flex flex-wrap">
            <Card  v-for="film in searchedFilms" :key="film.id" 
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

<style>
   
</style>