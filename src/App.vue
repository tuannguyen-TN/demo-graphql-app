<template>
	<div>
		<img src="/pokeball.svg" class="logo" alt="Pokeball logo" />
	</div>
	<div v-if="loading">Loading...</div>

	<div v-else-if="error">Error: {{ error.message }}</div>

	<div v-else-if="result && result.pokemons">
		<PokemonList :pokemons="pokemons" />
	</div>
</template>

<script setup lang="ts">
import { useQuery } from '@vue/apollo-composable'
import gql from 'graphql-tag'
import { computed } from 'vue'
import PokemonList from './components/PokemonList.vue'
import { Pokemon } from './types'

const query = gql`
	query getPokemons {
		pokemons(first: 7) {
			id
			name
			classification
			types
			image
		}
	}
`

const { result, loading, error } = useQuery(query)

const pokemons = computed((): Pokemon[] => {
	const list: Pokemon[] = []

	result.value?.pokemons.forEach((element: any) => {
		const name = element.name
		const classification = element.classification
		const types = element.types
		const image = element.image
		list.push({ name, classification, types, image })
	})

	return list
})
</script>

<style scoped>
.logo {
	height: 6em;
	padding: 1.5em;
	will-change: filter;
}
.logo:hover {
	filter: drop-shadow(0 0 2em #646cffaa);
}
</style>
