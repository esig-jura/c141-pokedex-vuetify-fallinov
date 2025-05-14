<template>
  <v-card :to="`/pokemons/${pokemon.id}`">
    <v-img
      alt="Magicarpe"
      height="200px"
      :src="`/images/${pokemon.img}`"
    />

    <v-card-title>
      {{ pokemon.name }}
    </v-card-title>

    <v-card-subtitle>
      Niveau: {{ pokemon.level }}
    </v-card-subtitle>

    <v-card-actions>
      <v-btn
        color="red"
        :icon="pokemonStore.isFavorite(pokemon) ? 'mdi-heart' : 'mdi-heart-outline'"
        @click.prevent="pokemonStore.toggleFavorite(pokemon)"
      />
    </v-card-actions>
  </v-card>
</template>

<script setup>
  import { usePokemonStore } from '@/stores/pokemonStore'
  import PokemonTypesChips from '@/components/PokemonTypesChips.vue'

  defineProps({
    pokemon: {
      type: Object,
      required: true,
    },
  })

  // Importer le magasin des pokémons
  const pokemonStore = usePokemonStore()
</script>

<style scoped>

</style>
