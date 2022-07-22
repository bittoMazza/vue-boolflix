<template>
    <div class="card-container">
        <img v-if="listItem.poster_path != null" :src="'https://image.tmdb.org/t/p/w342'+listItem.poster_path" class="poster-image text-white" alt="immagine Poster"> 
        <img v-else src="/no-poster.png" class="poster-image" alt="Poster non disponibile">
        <div class="card-content">
            <!-- Title è una proprità dei film,se non c'è o è undefined allora stiamo lavorando sulle serie -->
            <div v-if="listItem.title != null || listItem.title != undefined"> 
                <span class="d-block"><span class="card-info">Titolo</span> : {{ listItem.title }}</span>
                <span class="d-block"><span class="card-info">Titolo Originale</span> : {{ listItem.original_title}}</span>
            </div>
            <div v-else>
                <span class="d-block"><span class="card-info">Titolo</span> : {{ listItem.name }}</span>
                <span class="d-block"><span class="card-info">Titolo Originale</span> : {{ listItem.original_name}}</span>
            </div>
            <span v-if="convertVoteToStar(listItem.vote_average) != 0">
                <span class="card-info">Voto : <i v-for="(star,index) in convertVoteToStar(listItem.vote_average)" :key="index" class="bi bi-star-fill star-icon"></i></span>
            </span>
            <span v-else> NON CI SONO VOTI </span>
            <p class="card-overview"><span class="card-info">Overview</span> : {{ listItem.overview }}</p>
            <!-- <img :src="convertLangToFlag(listItem)" class="flag-image" alt="Bandiera non presente"><br>  -->         
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
        },
        checkPosterImg(item){
            if(item.title != null || item.title != undefined){
                return item.title
            }
            else{
                return item.name 
            }
        }
    }
}
</script>

<style lang="scss">
@import "../styles/variables.scss";
.flag-image{
        width:30px;
    }
.star-icon{
    font-size: 25px;
    color:rgb(219, 78, 12);
}
.poster-image{
    height: 100%;
    width: 100%;
}
.card-container{
    position:relative;
    border: 2px solid black;
    background-color: black;
    margin: 15px 5px;
    height: 500px;
    width: 342px;
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
        display: none;
        color: white;
        position: absolute;
        top: 20px;
        left: 20px;
        right: 20px;
        .card-info{
            font-weight: bold;
        }
        .card-overview{
            margin-top: 10px;
            height: 200px;
            overflow: auto;
            text-overflow: ellipsis;
        }
    }
    
    &:hover .poster-image{
        opacity: 0.1;
    }
    &:hover .card-content{
        display: block;
    }
}

</style>