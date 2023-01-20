<template>
	<div>
		<img src="/pokeball.svg" class="logo" alt="Pokeball logo" />
	</div>

	<h1>Welcome to Pokemon GraphQL</h1>

	<h1>Number of Pokemons: {{ num }}</h1>

	<PokemonList :number="num" />
</template>

<script setup lang="ts">
import { computed, ref } from 'vue'
import PokemonList from './components/PokemonList.vue'

const href = new URL(location.href).href

const num = computed((): number => {
	const splits = href.split('/')
	return Number(splits[splits.length - 1])
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
