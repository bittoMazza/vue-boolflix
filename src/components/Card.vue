<template>
<div class="d-flex flex-wrap">
    <div v-for="film in filmList" :key="film.id" class="card-container">
                <img :src="'https://image.tmdb.org/t/p/w185'+film.poster_path" class="w-100" alt="immagine poster"> 
                <span class="d-block">{{ film.title }}</span>
                <span class="d-block">{{ film.original_title}}</span>
                <img :src="convertLangToFlag(film)" class="flag-image d-block" alt="Bandiera non presente">
                <span v-if="convertVoteToStar(film.vote_average) != 0">
                    <i v-for="(star,index) in convertVoteToStar(film.vote_average)" :key="index" class="bi bi-star-fill star-icon"></i>
                </span>
                <span v-else> NON CI SONO VOTI </span>
    </div> 
     <div v-for="series in seriesList" :key="series.id" class="card-container">
                <img :src="'https://image.tmdb.org/t/p/w185'+series.poster_path" class="w-100" alt="immagine poster">
                <span class="d-block">{{ series.name }}</span>
                <span class="d-block">{{ series.original_name}}</span>
                <img :src="convertLangToFlag(series)" class="flag-image d-block" alt="Bandiera non presente">
                <span v-if="convertVoteToStar(series.vote_average) != 0">
                    <i v-for="(star,index) in convertVoteToStar(series.vote_average)" :key="index" class="bi bi-star-fill star-icon"></i>
                </span>
                <span v-else> NON CI SONO VOTI </span>
                
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
.star-icon{
    color:rgb(148, 148, 41);
}
.card-container{
    border:2px solid black;
    margin: 20px 10px;
    width:calc((100% / 6) - 20px);
}
</style>