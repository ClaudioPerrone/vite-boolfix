<script>
	import { store } from '../store.js';

    export default {
		name: 'CardFilm',

		props: {
			cardInfo: Object
		},

		data() {
			return {
				supportedFlags: [
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
			},
			
			getPosterUrl() {
				let posterImage = this.cardInfo.poster_path;

				return new URL(`https://image.tmdb.org/t/p/w154/${posterImage}`).href;
			},

			convertiVoto() {
				return Math.ceil(this.cardInfo.vote_average / 2);
    		}
		}
	}
</script>

<template>
	<ul class="result-card">
		<div class="poster">
			<li><img :src="getPosterUrl()"></li>
		</div>
		<div class="info">
			<li><h3>Titolo: "{{ cardInfo.title }} {{ cardInfo.name }}"</h3></li>
			<li><h2>Titolo originale: "{{ cardInfo.original_title }} {{ cardInfo.name }}"</h2></li>
			<li>
				<p>Lingua: <img class="flag" :src="getFlagUrl()"></p>
			</li>
			<li><p>Voto:
				<!-- {{ convertiVoto() }} -->
				<i v-for="n in convertiVoto()" class="fa-solid fa-star"></i>
				<i v-for="n in 5 - convertiVoto()" class="fa-regular fa-star"></i>
			</p></li>
		</div>
	</ul>
</template>

<style scoped lang="scss">
.result-card {
	height: 250px;

	li {
		list-style-type: none;

		p {
			display: inline;
		}
		
		.flag {
			width: 25px;
		}
	}
	.poster {
		display: block;
	}

	
	&:hover .poster{
			display: none;
		}

	.info {
		display: none;
	}

	&:hover .info{
		display: block;
	}

}

</style>