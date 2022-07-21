<template>
    <div>
        <h2>Film</h2>
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