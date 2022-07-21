<template>
    <div>
        <div v-for="film in searchedFilms" class="p-3" :key="film.id">
                <span class="d-block">{{ film.title }}</span>
                <span class="d-block">{{ film.original_title}}</span>
                <!-- <img :src="film.poster_path" class="d-block"> -->
                <span class="d-block">{{ film.vote_average }}</span>
        </div> 
    </div>
</template>

<script>
export default {
     props:{
        searchedFilms:Array,
    }
}
</script>

<style>

</style>