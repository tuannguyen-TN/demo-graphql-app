<template>
	<div class="list-container">
		<ul v-for="(pokemon, index) in pokemons" :key="index" style="list-style: none; padding: 0">
			<li>
				<h1>{{ pokemon.name }}</h1>
			</li>
			<li>
				<h2>Classification</h2>
				{{ pokemon.classification }}
			</li>
			<li>
				<h2>Types</h2>
				{{ pokemon.types }}
			</li>
			<li><img :src="pokemon.image" :alt="pokemon.name" /></li>
		</ul>
	</div>
</template>

<script setup lang="ts">
import { computed, PropType } from 'vue'
import { Pokemon } from '../types'

const props = defineProps({
	pokemons: {
		type: Array as PropType<Pokemon[] | null>,
	},
})
</script>

<style scoped>
.list-container {
	align-items: center;
}
</style>
