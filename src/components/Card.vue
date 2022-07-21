<template>
    <div class="card-container">
        <img :src="'https://image.tmdb.org/t/p/w185'+listItem.poster_path" class="w-100" alt="immagine poster"> 
        <div v-if="listItem.title != null || listItem.title != undefined">
            <span class="d-block">{{ listItem.title }}</span>
            <span class="d-block">{{ listItem.original_title}}</span>
        </div>
        <div v-else>
            <span class="d-block">{{ listItem.name }}</span>
            <span class="d-block">{{ listItem.original_name}}</span>
        </div>
        <img :src="convertLangToFlag(listItem)" class="flag-image d-block" alt="Bandiera non presente">
        <span v-if="convertVoteToStar(listItem.vote_average) != 0">
            <i v-for="(star,index) in convertVoteToStar(listItem.vote_average)" :key="index" class="bi bi-star-fill star-icon"></i>
        </span>
        <span v-else> NON CI SONO VOTI </span>
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
        listItem:Object
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