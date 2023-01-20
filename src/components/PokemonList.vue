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
		type: Number as PropType<number | null>,
	},
})

console.log(props.number)

const query = gql`
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

const { result, loading, error } = useQuery(query, {
	num: props.number,
})

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
.list-container {
	align-items: center;
}
</style>
