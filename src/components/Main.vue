<template>
    <main>
        <div v-for="film in searchedListElement" :key="film.id">
            <span>{{ film.title }}</span>
            <span>{{ film.original_title}}</span>
            <span>{{ film.original_language }}</span>
            <span>{{ film.vote_average }}</span>
        </div>
    </main>
</template>

<script>
export default {
 props:['searchedListElement'],
}
</script>

<style>

</style>