<template>
	<div class="list-container">
		<ul v-for="(pokemon, index) in pokemons" :key="index" style="list-style: none; padding: 0">
			<li>
				<h1>{{ pokemon.name }}</h1>
			</li>
			<li>
				<h2>Classification:</h2>
				{{ pokemon.classification }}
			</li>
			<li>
				<h2>Types:</h2>
				{{ pokemon.types }}
			</li>
			<li><img :src="pokemon.image" :alt="pokemon.name" /></li>
		</ul>
	</div>
</template>

<script setup lang="ts">
import { useQuery } from '@vue/apollo-composable'
import gql from 'graphql-tag'
import { computed, PropType } from 'vue'
import { Pokemon } from '../types'

const props = defineProps({
	number: {
		type: Number,
	},
	name: {
		type: String,
	}
})

const listQuery = gql`
	query getPokemons($num: Int!) {
		pokemons(first: $num) {
			id
			name
			classification
			types
			image
		}
	}
`

const searchQuery = gql`
	query getPokemon($name: String) {
		pokemon(name: $name) {
			id
			name
			classification
			types
			image
		}
	}
`

const { result, loading, error } = props.name ? useQuery(searchQuery, {
	name: props.name
}) : useQuery(listQuery, {
	num: props.number
})

const pokemons = computed((): Pokemon[] => {
	const list: Pokemon[] = []

	const resultList = props.name ? [result.value?.pokemon] : result.value?.pokemons

	resultList?.forEach((element: any) => {
		const name = element?.name
		const classification = element?.classification
		const types = element?.types
		const image = element?.image
		list.push({ name, classification, types, image })
	})

	return list
})
</script>

<style scoped>
.list-container {
	align-items: center;
}
</style>
