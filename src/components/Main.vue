<template>
    <main>
        <div class="container-elements">
             <FilmList v-show="searchedFilmList != 0"
             :searchedFilms="searchedFilmList"/>
             <SeriesList  v-show="searchedSeriesList != 0"
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
.container-elements{
    margin: 0 100px;
}

</style>
