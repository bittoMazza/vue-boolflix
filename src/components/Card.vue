<template>
    <div class="card-container">
        <img :src="'https://image.tmdb.org/t/p/w342'+listItem.poster_path" class="img-fluid poster-image" alt="Poster Mancante"> 
        <div class="card-content">
            <div v-if="listItem.title != null || listItem.title != undefined"> <!-- Title è una proprità dei film,se non c'è o è undefined allora stiamo lavorando sulle serie -->
                <span class="d-block"><span class="card-info">Titolo</span> : {{ listItem.title }}</span>
                <span class="d-block"><span class="card-info">Titolo Originale</span> : {{ listItem.original_title}}</span>
            </div>
            <div v-else>
                <span class="d-block"><span class="card-info">Titolo</span> : {{ listItem.name }}</span>
                <span class="d-block"><span class="card-info">Titolo Originale</span> : {{ listItem.original_name}}</span>
            </div>
            <span v-if="convertVoteToStar(listItem.vote_average) != 0">
                <i v-for="(star,index) in convertVoteToStar(listItem.vote_average)" :key="index" class="bi bi-star-fill star-icon"></i>
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
        }  
    }
}
</script>

<style lang="scss">
.flag-image{
        width:30px;
    }
.star-icon{
    font-size: 25px;
    color:rgb(219, 78, 12);
}
.card-container{
    position:relative;
    background-color: black;
    margin: 20px 10px;
    width:calc((100% / 4) - 20px);
        ::-webkit-scrollbar {
        width: 12px;
    }

    ::-webkit-scrollbar-track {
        -webkit-box-shadow: inset 0 0 6px rgba(245, 19, 19, 0.3); 
        border-radius: 10px;
    }

    ::-webkit-scrollbar-thumb {
        border-radius: 10px;
        background: rgb(238, 32, 32); 
    }
    .card-content{
        display: none;
        color: white;
        position: absolute;
        top: 30px;
        left: 20px;
        right: 20px;
        .card-info{
            font-weight: bold;
        }
        .card-overview{
            margin-top: 10px;
            height: 300px;
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