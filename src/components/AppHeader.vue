<script>
	import { store } from '../store.js';

    export default {
		name: "AppHeader",
		data() {
			return {
				store
			};
		}
	}

</script>

<template>
	<header>
		<input type="text" v-model="store.searchText">
		<button @click="$emit('searchPerformed')">Cerca</button>
	</header>
</template>

<style scoped lang="scss">
header {
	background-color: brown;
	padding: 20px;
}

</style>