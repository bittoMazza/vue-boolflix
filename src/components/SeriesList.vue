<template>
  <div>
    <h2>Serie</h2>
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
    props:{
        searchedSeries:Array,
    },
     methods:{
        convertLangToFlag(singleSeries){
            if(this.languageArray.includes(singleSeries.original_language))
            {
                   return "/flag/"+singleSeries.original_language+".png"
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