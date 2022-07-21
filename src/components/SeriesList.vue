<template>
  <div>
    <h2>Serie</h2>
        <div v-for="series in searchedSeries" class="p-3" :key="series.id">
                <span class="d-block">{{ series.name }}</span>
                <span class="d-block">{{ series.original_name}}</span>
                <!-- <img :src="film.poster_path" class="d-block"> -->
                <span class="d-block">{{ series.vote_average }}</span>
        </div> 
    </div>
</template>

<script>
export default {
    props:{
        searchedSeries:Array,
    }
}
</script>

<style>

</style>