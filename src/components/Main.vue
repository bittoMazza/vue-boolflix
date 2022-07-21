<template>
    <main>
        <FilmList
         :searchedFilms="searchedFilmList"/>
        <SeriesList
         :searchedSeries="searchedSeriesList"     
        />
    </main>
</template>

<script>
import FilmList from "./FilmList.vue"
import SeriesList from "./SeriesList.vue"

export default {
 props:{
    searchedFilmList:Array,
    searchedSeriesList:Array,
    },
 components:{
    FilmList,
    SeriesList,
 }
}
</script>

<style>

</style>
