<template>
    <div>
        <h2>Film</h2>
        <div v-for="film in searchedFilms" class="p-3" :key="film.id">
                <span class="d-block">{{ film.title }}</span>
                <span class="d-block">{{ film.original_title}}</span>
                <img :src="convertLangToFlag(film)" class="flag-image" alt="Bandiera non presente">
                <span class="d-block">{{ film.vote_average }}</span>
        </div> 
    </div>
</template>

<script>
export default {
    data:function(){
        return{
            languageArray:['it','de','en','pt'],
          
        }
    },
     props:{
        searchedFilms:Array,
    },
    methods:{
        convertLangToFlag(singleFilm){
            if(this.languageArray.includes(singleFilm.original_language))
            {
                   return "/flag/"+singleFilm.original_language+".png"
            }
          
        }   
    }
}
</script>

<style>
    .flag-image{
        width:30px;
    }
</style>