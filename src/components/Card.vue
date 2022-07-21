<template>
<div>
    <div v-for="film in searchedFilms" class="p-3" :key="film.id">
                <span class="d-block">{{ film.title }}</span>
                <span class="d-block">{{ film.original_title}}</span>
                <img :src="convertLangToFlag(film)" class="flag-image" alt="Bandiera non presente">
                <span class="d-block">{{ film.vote_average }}</span>
    </div> 
     <div v-for="series in searchedSeries" class="p-3" :key="series.id">
                <span class="d-block">{{ series.name }}</span>
                <span class="d-block">{{ series.original_name}}</span>
                <img :src="convertLangToFlag(series)" class="flag-image" alt="Bandiera non presente">
                <span class="d-block">{{ series.vote_average }}</span>
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
     methods:{
        convertLangToFlag(singleElement){
            if(this.languageArray.includes(singleElement.original_language))
            {
                   return "/flag/"+singleElement.original_language+".png"
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