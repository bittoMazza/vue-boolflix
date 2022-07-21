<template>
  <header>
    <div class="search-container">
        <input type="text" v-model="searchedElement" placeholder="Scrivi quale film vuoi cercare">
        <button @click="searchFilmName"> CERCA </button>
    </div>
  </header>
</template>

<script>
import axios from 'axios';
export default {
    data:function(){
        return{
            searchedElement:''
        }   
    },
    methods:{
        searchFilmName(){
            if(this.searchedElement == null || this.searchedElement == ''){
                alert('Inserisci il nome del film da cercare')
            }
            else{
                 axios.get('https://api.themoviedb.org/3/search/movie?api_key=f6a28c97150ef559daa0a8f32bc1fee9&&query='+this.searchedElement) // Cerchiamo per titolo
                .then( (result) => {   
                        console.log(result);    
                        })                   
                    .catch((error) => {
                        console.warn(error)
                    })
            }
           
        }
    }
}
</script>

<style lang="scss">

</style>