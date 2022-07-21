<template>
  <div id="app">
    <Header
    @selectElement="SearchFilmName"
    />
    <Main
    :searchedListElement="searchedListElement"
    :completedPath="completedPath"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"
import axios from 'axios';


export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data:function(){
    return{
      searchedListElement:[],
      urlPathFilm:'https://api.themoviedb.org/3/search/movie?api_key=f6a28c97150ef559daa0a8f32bc1fee9&&query=',
      urlPathTV:'https://api.themoviedb.org/3/search/tv?api_key=f6a28c97150ef559daa0a8f32bc1fee9&&query=',
      completedPath:'',
    }
  },
  methods:{
    SearchFilmName(searchedFilm){
            if(searchedFilm == null || searchedFilm == ''){
                alert('Inserisci il nome del film da cercare')
            }
            else{
                 axios.get(this.urlPath+searchedFilm) // Cerchiamo per titolo
                .then( (result) => {   
                        this.completedPath = this.urlPath+searchedFilm
                        this.searchedListElement = result.data.results;  
                        console.log(this.searchedListElement)
                        })                   
                    .catch((error) => {
                        console.warn(error)
                    })
            }
           
        },
    SearchSerieName(searchSeries){
      
    }
  }
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";
</style>
