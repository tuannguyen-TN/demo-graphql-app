<template>
	<div>
		<img src="/pokeball.svg" class="logo" alt="Pokeball logo" />
	</div>

	<h1>Welcome to GraphQL Pokemon App</h1>

	<h1>Number of Pokemons: {{ fetchArguments.numPokemon }}</h1>

	<PokemonList :number="fetchArguments.numPokemon" :name="fetchArguments.pokemonName" />
</template>

<script setup lang="ts">
import { computed, ref } from 'vue'
import PokemonList from './components/PokemonList.vue'

const href = new URL(location.href).href

const fetchArguments = computed((): {numPokemon: number, pokemonName: string} => {
	let num: number = 0
	let name: string = ''

	const args = href.split('/').slice(-2)
	if (args[0] == 'list' && !isNaN(Number(args[1]))) {
		num = Number(args[1])
	} else if (args[0] == 'search' && args[1]) {
		num = 1
		name = args[1]
	}

	return {
		numPokemon: num,
		pokemonName: name
	}
})
</script>

<style scoped>
.logo {
	height: 6em;
	will-change: filter;
}
.logo:hover {
	filter: drop-shadow(0 0 2em #646cffaa);
}
</style>
