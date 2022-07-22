<template>
    <main>
        <div class="container">
             <FilmList 
             :searchedFilms="searchedFilmList"/>
             <SeriesList
             :searchedSeries="searchedSeriesList"     
             />
        </div>
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

<style lang="scss">
@import "../styles/variables.scss";
// Style for both menu horizontal scroll


</style>
