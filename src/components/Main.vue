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
.scrollmenu {
  overflow-x: auto;
  white-space: nowrap;
}
.scroll-style{
     ::-webkit-scrollbar {
        width: 12px;
    }

    ::-webkit-scrollbar-track {
        -webkit-box-shadow: inset 0 0 6px rgba(245, 19, 19, 0.3); 
        border-radius: 10px;
    }

    ::-webkit-scrollbar-thumb {
        border-radius: 10px;
        background:$mainColor; 
    }
}

</style>
