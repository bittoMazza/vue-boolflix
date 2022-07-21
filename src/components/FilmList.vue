<template>
    <div>
        <h2>Film</h2>
        <Card/>
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