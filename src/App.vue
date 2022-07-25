<template>
  <div id="app">
    <Header
    @selectElement="SearchElementsName"
    />
    <Main
    :searchedFilmList="searchedFilmList"
    :searchedSeriesList="searchedSeriesList"
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
      searchedFilmList:[],
      searchedSeriesList:[],
      urlPathFilm:'https://api.themoviedb.org/3/search/movie?api_key=f6a28c97150ef559daa0a8f32bc1fee9&&language=it-IT&query=',
      urlPathTV:'https://api.themoviedb.org/3/search/tv?api_key=f6a28c97150ef559daa0a8f32bc1fee9&&language=it-IT&query=',
    }
  },
  methods:{
    SearchElementsName(Element){
            if(Element == null || Element == ''){
                alert('Inserisci il nome del film/serie da cercare')
            }
            else{
                 axios.get(this.urlPathFilm+Element) // Facciamo una ricerca nei film e popoliamo il suo array
                .then( (result) => {   
                        this.searchedFilmList = result.data.results; 
                        console.log(this.searchedFilmList) 
                        })                   
                    .catch((error) => {
                        console.warn(error)
                    })
                axios.get(this.urlPathTV+Element) // Facciamo una ricerca nelle serie e popoliamo il suo array
                .then( (result) => {   
                        this.searchedSeriesList = result.data.results;  
                        })                   
                    .catch((error) => {
                        console.warn(error)
                    })
            }
           
        },
  }
}
</script>

<style lang="scss">
@import "./styles/variables.scss";
@import "~bootstrap-icons/font/bootstrap-icons.css"; 
@import "~bootstrap/scss/bootstrap.scss";
body{
  background-color: $mainBg;
}
</style>
