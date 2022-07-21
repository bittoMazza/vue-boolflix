<template>
    <main>
        
    </main>
</template>

<script>
import FilmList from "./FilmList.vue"
import SeriesList from "./SeriesList.vue"

export default {
 props:{
    searchedListElement:Array,
    completedPath:String,
    },
 components:{
    FilmList,
    SeriesList,
 }
}
</script>

<style>

</style>

/* <div v-for="film in searchedListElement" class="p-3" :key="film.id">
            <span class="d-block">{{ film.title }}</span>
            <span class="d-block">{{ film.original_title}}</span>
            <!-- <img :src="film.poster_path" class="d-block"> -->
            <span class="d-block">{{ film.vote_average }}</span>
        </div> */