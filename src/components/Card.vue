<template>
<div>
    <div v-for="film in filmList" class="p-3" :key="film.id">
                <img :src="elementPoster+film.poster_path" alt="immagine poster">
                <span class="d-block">{{ film.title }}</span>
                <span class="d-block">{{ film.original_title}}</span>
                <img :src="convertLangToFlag(film)" class="flag-image d-block" alt="Bandiera non presente">
                <i v-for="(star,index) in convertVoteToStar(film.vote_average)" :key="index" class="bi bi-star-fill"></i>
    </div> 
     <div v-for="series in seriesList" class="p-3" :key="series.id">
                <img :src="elementPoster+series.poster_path" alt="immagine poster">
                <span class="d-block">{{ series.name }}</span>
                <span class="d-block">{{ series.original_name}}</span>
                <img :src="convertLangToFlag(series)" class="flag-image" alt="Bandiera non presente">
                <i v-for="(star,index) in convertVoteToStar(series.vote_average)" :key="index" class="bi bi-star-fill"></i>
        </div> 
</div>
  
</template>

<script>
export default {
     data:function(){
        return{
            languageArray:['it','de','en','pt'], 
            elementPoster:"https://image.tmdb.org/t/p/w342" 
        }
    },
    props:{
        seriesList:Array,
        filmList:Array,
    },
     methods:{
        convertLangToFlag(singleElement){
            if(this.languageArray.includes(singleElement.original_language))
            {
                   return "/flag/"+singleElement.original_language+".png"
            }
          
        } ,
        convertVoteToStar(vote){
           const starVote = vote / 2
           return Math.ceil(starVote);
        }  
    }
}
</script>

<style>
 .flag-image{
        width:30px;
    }
</style>