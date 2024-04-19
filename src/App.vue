<script>
    import { store } from './store.js';
    import axios from 'axios';
    import AppHeader from './components/AppHeader.vue';
    import ListFilms from './components/ListFilms.vue';

    export default {

        components: {
            AppHeader,
            ListFilms
        },

        data() {
            return {
	            store
	        };
        },

        methods: {
            getFilmFromApi() {
                //console.log('chiamata api');
                const queryParams = {
                    api_key: store.apiKey,
                    query: store.searchText
                };

                axios.get('https://api.themoviedb.org/3/search/movie', {
	                params:queryParams
	            }).
	            then((response) => {
                    console.log(store.movies);
	                store.movies = response.data.results;
	            });

            },
        }
    }

</script>

<template>
    <AppHeader @searchPerformed="getFilmFromApi"></AppHeader>

    <main>
        <ListFilms></ListFilms>
    </main>
</template>

<style lang="scss">
    @use './style/generics';
</style>
