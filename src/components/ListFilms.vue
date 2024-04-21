<script>
    import { store } from '../store.js';
    import CardFilm from './CardFilm.vue';

    export default {
		name: "ListFilms",

        data() {
            return {
                store
            }
        },
        
        components: {
            CardFilm
        }
	}
</script>

<template>
    <section>
        <h2>Film</h2>
        <CardFilm v-for="movie in store.movies" :key="movie.id" :cardInfo="movie"></CardFilm>
    </section>
    <section>
        <h2>Serie TV</h2>
        <CardFilm v-for="serie in store.series" :key="serie.id" :cardInfo="serie"></CardFilm>
    </section>
</template>

<style scoped lang="scss">

</style>