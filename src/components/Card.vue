<template>
    <div class="card-container">
        <img v-if="listItem.poster_path != null" :src="'https://image.tmdb.org/t/p/w342'+listItem.poster_path" class="poster-image text-white" alt="immagine Poster"> 
        <img v-else src="/no-poster.png" class="poster-image" alt="Poster non disponibile">
        <div class="card-content">
            <!-- Title è una proprità dei film,se non c'è o è undefined allora stiamo lavorando sulle serie -->
            <div>
                <span class="d-block py-1"><span class="card-info">Titolo</span> : {{ getTitle(listItem) }}</span>
                <span class="d-block py-1"><span class="card-info">Titolo Originale</span> : {{ getOriginalTitle(listItem) }}</span>
            </div>
            <span v-if="convertVoteToStar(listItem.vote_average) != 0">
                <span class="card-info py-1">Voto : <i v-for="(star,index) in convertVoteToStar(listItem.vote_average)" :key="index" class="bi bi-star-fill star-icon"></i></span><br>
            </span>
            <span v-else class="py-1"> NON CI SONO VOTI </span><br>
            <img :src="convertLangToFlag(listItem)" class="flag-image" :alt="'lingua originale : '+ listItem.original_language ">  
            <p class="card-overview"><span class="card-info">Overview</span> : {{ listItem.overview }}</p>    
            <p v-if="listItem.title != null || listItem.title != undefined">
                <span class="text-white" v-for="(cast,index) in getCast('movie',listItem.id) " :key="index">
                 pappa
                </span>
            </p>
            <p v-else>
                 <span class="text-white" v-for="(cast,index) in getCast('tv',listItem.id) " :key="index">
                   pappa
                </span>
            </p>
        </div>       
    </div>
</template>

<script>
import axios from 'axios';
export default {
     data:function(){
        return{
            languageArray:['it','de','en','pt'], 
        }
    },
    props:{
        listItem:Object,
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
        },
        getTitle(item){
            if( item.title != null || item.title != undefined)
            {
                return item.title
            }
            return item.name
        },
        getOriginalTitle(item){
             if( item.title != null || item.title != undefined)
            {
                return item.original_title
            }
            return item.original_name
        },
        getCast(typeElement,idElement){
            axios.get(`https://api.themoviedb.org/3/${typeElement}/${idElement}/credits?api_key=f6a28c97150ef559daa0a8f32bc1fee9`)
                .then( (result) => {   
                        let castList = result.data.cast; 
                        console.log(castList.slice(0,5))
                        return castList.slice(0,5)
                        })         
     
        },

    }
}
</script>

<style lang="scss" scoped>
@import "../styles/variables.scss";
.flag-image{
        width:30px;
    }
.star-icon{
    font-size: 25px;
    color:rgb(219, 78, 12);
}
.poster-image{
    backface-visibility: hidden;
    height: 100%;
    width: 100%;
}
.card-container{
    position:relative;
    transition: transform 0.5s;
    transform-style: preserve-3d;
    border: 2px solid black;
    background-color: black;
    margin: 15px 5px;
    width: calc((100% / 6) - 10px);
    &:hover .poster-image{
        opacity: 0.1;
    }
    &:hover {
         transform: rotateY( 180deg ) ;
         transition: transform 1s;
    }
    &:hover .card-content{
        display: block;
    }
        ::-webkit-scrollbar {
        width: 12px;
    }

    ::-webkit-scrollbar-track {
        -webkit-box-shadow: inset 0 0 6px rgba(245, 19, 19, 0.3); 
        border-radius: 10px;
    }

    ::-webkit-scrollbar-thumb {
        border-radius: 10px;
        background:$mainColor; 
    }
    .card-content{
        backface-visibility: hidden;
        transform: rotateY( 180deg );
        display: none;
        color: white;
        position: absolute;
        top: 10px;
        left: 10px;
        right: 20px;
        .card-info{
            font-weight: bold;
        }
        .card-overview{
            margin-top: 10px;
            height: 80px;
            overflow-y: scroll;
            text-overflow: ellipsis;
        }
    }
    
}
   @media screen and (max-width: 1600px) {
    .card-container {
      width: calc((100% / 4) - 10px);
        }
    }
    @media screen and (max-width: 1190px) {
    .card-container {
      width: calc((100% / 3) - 10px);
        }
    }
    .card-overview{
        height: 200px;
    }
     @media screen and (max-width: 970px) {
    .card-container {
      width: calc((100% / 2) - 10px);
        }
    }
</style>