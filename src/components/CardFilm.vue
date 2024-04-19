<script>
	import { store } from '../store.js';

    export default {
		name: 'CardFilm',
		props: {
			cardInfo: Object
		},
		data() {
        	return {
	    		store
        	}
    	}
	}
</script>

<template>
	<ul>
		<li><h3>Titolo: "{{ cardInfo.title }}"</h3></li>
		<li><h2>Titolo originale: "{{ cardInfo.original_title }}"</h2></li>
		<li><p>Lingua: {{ cardInfo.original_language }}</p></li>
		<li><p>Voto: {{ cardInfo.vote_average }}</p></li>
	</ul>
</template>

<style scoped lang="scss">
	li {
		list-style-type: none;
	}
</style>