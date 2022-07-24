<template>
    <main>
        <div class="container-elements">
            <h2 class="text-center text-white"> </h2>
            <div class="py-5" v-show="searchedFilmList != 0">
                <h2 class="text-white text-start display-2 text-center">FILM</h2>
                <ElementsList
                :searchedElements="searchedFilmList"/>
            </div>
            <div class="py-5"  v-show="searchedSeriesList != 0">
                <h2 class="text-white text-start display-2 text-center">SERIE TV</h2>
                 <ElementsList
                :searchedElements="searchedSeriesList"     
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
}

</style>
