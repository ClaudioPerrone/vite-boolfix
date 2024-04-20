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
        <CardFilm v-for="movie in store.movies" :key="movie.id" :cardInfo="movie"></CardFilm>
    </section>
</template>

<style scoped lang="scss">

</style>