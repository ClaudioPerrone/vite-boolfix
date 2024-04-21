<!-- 
    Esercizio di oggi: Boolflix

    https://docs.google.com/document/d/1JBwSbzVo88GBKKUwNTx6fQe7RetT_uw_PTxtGgoQPWI/edit
 -->


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

        methods: {
            getFilmFromApi() {
                //console.log('chiamata api');
                const queryParams = {
                    api_key: store.apiKey,
                    query: store.searchText
                };

                //Sezione per i film
                axios.get('https://api.themoviedb.org/3/search/movie', {
	                params: queryParams
	                }).
	                then((response) => {
                        //console.log(store.movies);
	                    store.movies = response.data.results;
	            });
            },

            getSeriesFromApi() {
                //console.log('chiamata api');
                const queryParams = {
                    api_key: store.apiKey,
                    query: store.searchText
                };

                //Sezione per le serie
                axios.get('https://api.themoviedb.org/3/search/tv', {
	                params: queryParams
	                }).
	                then((response) => {
                        //console.log(store.series);
	                    store.series = response.data.results;
	            });
            },

            getMovieAndSeries() {
                this.getFilmFromApi();
                this.getSeriesFromApi();
            }
        }
    }
</script>

<template>
    <AppHeader @searchPerformed="getMovieAndSeries"></AppHeader>

    <main>
        <ListFilms></ListFilms>
    </main>
</template>

<style lang="scss">
    @use './style/generics';
</style>
