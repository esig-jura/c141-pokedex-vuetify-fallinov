<template>
  <v-container>
    <h1 class="mb-6 text-center">Pokédex</h1>

    <v-text-field
      v-model="search"
      clearable
      label="Rechercher un Pokémon"
      prepend-icon="mdi-magnify"
    />

    <v-alert v-if="filteredPokemons.length === 0" class="text-center mt-4" type="warning">
      Aucun Pokémon ne correspond à votre recherche.
    </v-alert>

    <v-row v-else>
      <!-- Exemple de colonne vide (à dupliquer plus tard avec du contenu) -->
      <v-col
        v-for="pokemon in filteredPokemons"
        :key="pokemon.id"
        cols="12"
        lg="3"
        md="4"
        sm="6"
        xl="2"
        xs="12"
      >
        <pokemon-card :pokemon="pokemon" />
      </v-col></v-row>
  </v-container>
</template>

<script setup>
  // Importer le magasin des pokémons
  // @/ => représente le dossier src
  import { usePokemonStore } from '@/stores/pokemonStore'
  import PokemonCard from '@/components/PokemonCard.vue'

  // Récupère le magasin des Pokémon
  const pokemonStore = usePokemonStore()

  // Texte du champ de recherche
  const search = ref('')

  // Propriété calculée pour filtrer les Pokémon en fonction de la recherche
  const filteredPokemons = computed(() => {
    const query = search.value.toLowerCase().trim()
    return pokemonStore.pokemons.filter(pokemon =>
      pokemon.name.toLowerCase().includes(query)
    )
  })
</script>

<style scoped>
/* Animation pour l'icône de favori */
:deep(.mdi-heart) {
  animation: heartbeat 1s ease-in-out;
}
</style>
