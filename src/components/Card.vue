<template>
    <div class="card-container" :style="{backgroundImage:`url(${posterImage})`}">
        <img class="poster-img" :src="'https://image.tmdb.org/t/p/w342'+listItem.poster_path"  alt="immagine poster non presente"> 
        <div class="d-none"> 
            <div v-if="listItem.title != null || listItem.title != undefined"> <!-- Title è una proprità dei film,se non c'è o è undefined allora stiamo lavorando sulle serie -->
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
    </div>
</template>

<script>
export default {
     data:function(){
        return{
            languageArray:['it','de','en','pt'], 
            posterImage:'https://image.tmdb.org/t/p/w342'+this.listItem.poster_path,
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

<style lang="scss">
.flag-image{
        width:30px;
    }
.star-icon{
    color:rgb(148, 148, 41);
}
.card-container{
    background-image: var();
    background-color: grey;
    background-size: cover;
    margin: 20px 10px;
}

</style>