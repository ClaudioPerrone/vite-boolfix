<script>
	import { store } from '../store.js';

    export default {
		name: 'CardFilm',

		props: {
			cardInfo: Object
		},

		data() {
			return {
				supportedFlas: [
					'en',
					'fr',
					'it'
				]
			};
		},

		methods: {
			getFlagUrl() {
				let flagImageName;

				if(this.cardInfo.original_language === 'en') {
					flagImageName = 'england.png';
				} else if(this.cardInfo.original_language === 'fr') {
					flagImageName = 'france.png';
				} else if(this.cardInfo.original_language === 'it') {
					flagImageName = 'italy.png';
				}

				return new URL(`../assets/images/${flagImageName}`, import.meta.url).href;
			}
		}
	}
</script>

<template>
	<ul>
		<li><h3>Titolo: "{{ cardInfo.title }}"</h3></li>
		<li><h2>Titolo originale: "{{ cardInfo.original_title }}"</h2></li>
		<li>
			<p>Lingua: <img :src="getFlagUrl()"> {{ cardInfo.original_language }}</p>
		</li>
		<li><p>Voto: {{ cardInfo.vote_average }}</p></li>
	</ul>
</template>

<style scoped lang="scss">
	li {
		list-style-type: none;

		p {
			display: inline;
		}
		
		img {
			width: 25px;
		}
	}
</style>