<template>
    <main>
        <div class="container-elements">
            <div class="mt-5" id="film-list"> 
                <a v-show="searchedFilmList != 0"  class="anchor" href="#film-list">FILM</a>
                <a v-show="searchedSeriesList != 0" class="anchor" href="#series-list">SERIE TV</a>
            </div>
            <div class="py-5" v-show="searchedFilmList != 0" id="film-list">
                <h2 class="text-white text-start display-2 text-center">FILM</h2>
                <ElementsList
                :searchedElements="searchedFilmList"
                :searchedCast="searchedFilmActors"/>
                
                
            </div>
            <div class="py-5" v-show="searchedSeriesList != 0" id="series-list">
                <h2 class="text-white text-start display-2 text-center">SERIE TV</h2>
                 <ElementsList
                :searchedElements="searchedSeriesList"     
                :searchedCast ="searchedSeriesActors"
                />
            </div>
            
        </div>
    </main>
</template>

<script>
import ElementsList from "./ElementsList.vue"

export default {
 props:{
    searchedFilmList:Array,
    searchedSeriesList:Array,
    searchedFilmActors:Array,
    searchedSeriesActors:Array
    },
 components:{
    ElementsList,
 }
}
</script>

<style lang="scss">
@import "../styles/variables.scss";
// Style for both menu horizontal scroll
.container-elements{
    margin: 0 100px;

    .anchor{
        text-decoration: none;
        color: white;
        padding: 10px 15px;
        text-align: center;
        background-color: grey;
        border-radius: 10px;
        margin: 0 10px;
        letter-spacing: 2px;
    }
}

</style>
