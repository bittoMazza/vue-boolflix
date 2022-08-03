<template>
    <div class="card-container d-inline-block">
        <img v-if="listItem.poster_path != null" :src="'https://image.tmdb.org/t/p/w342'+listItem.poster_path" class="poster-image text-white" alt="immagine Poster"> 
        <img v-else src="/no-poster.png" class="poster-image" alt="Poster non disponibile">
        <div class="card-content">
            <div>
                <span class="d-block "><span class="card-info main-text-color">Titolo</span> : {{ getTitle(listItem) }}</span>
                <span class="d-block "><span class="card-info ">Titolo Originale</span> : {{ getOriginalTitle(listItem) }}</span>
            </div>
            <span v-if="convertVoteToStar(listItem.vote_average) != 0">
                <span class="card-info py-1">Voto : <i v-for="(star,index) in convertVoteToStar(listItem.vote_average)" :key="index" class="bi bi-star-fill star-icon"></i></span>
            </span>
            <span v-else class="py-1"> NON CI SONO VOTI </span><br>
            <img :src="convertLangToFlag(listItem)" class="flag-image" :alt="'lingua originale : '+ listItem.original_language ">  
            <p class="card-overview" v-if="listItem.overview != ''"><span class="card-info">Overview</span> : {{ listItem.overview }}</p>   
            <span v-else class="d-block py-2 fw-bold main-text-color">LA TRAMA NON E' PRESENTE</span> 
            <p>
                <span class="card-info text-white">Cast : </span>
                <span class="text-white"  v-for="(Actors,index) in searchedListCast[searchedCastIndex]" :key="index">
                 {{Actors.name}},
                </span>
            </p>
            <p>
                <span class="card-info text.white">Generi : </span>
                <span class="text-white" v-for="(genre,index) in listItem.genre_ids" :key="index" >
                    {{ getGenre(genre,listItem.genre_ids) }},
                </span>
            </p>
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
        listItem:Object,
        searchedListCast:Array,
        searchedCastIndex:Number,
        genreListElement:Array,
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
        getGenre(singleGenre){
            console.log(singleGenre)
            for(let i=0;i < this.genreListElement.length ;i++)
            {
                if(singleGenre  === this.genreListElement[i].id)
                {
                    return this.genreListElement[i].name
                }
            }
        },

    },
  
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
    width: calc((100% / 5) - 10px);
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
        -webkit-box-shadow: inset 0 0 6px rgba(245, 19, 19); 
        border-radius: 10px;
    }

    ::-webkit-scrollbar-thumb {
        border-radius: 10px;
        background:$mainColor; 
    }
    .card-content{
        white-space:pre-wrap;
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
            height:75px;
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
    @media screen and (max-width: 1350px) {
    .card-container {
      width: calc((100% / 3) - 10px);
        }
    }
    .card-overview{
        height: 200px;
    }
     @media screen and (max-width: 1090px) {
    .card-container {
      width: calc((100% / 2) - 10px);
        }
    }
</style>