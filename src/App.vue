<template>
  <!--
  Conteneur principal de l'application utilisant Vuetify
    * <v-app> est l'enveloppe principale pour l'intégration des composants Vuetify
  -->
  <v-app>
    <!--
    Menu principal
      * Affiche la barre de navigation principale (header)
      * Inclut le composant personnalisé MenuPrincipal créer dans le fichier `src/components/AppHeader.vue`
    -->
    <menu-principal />
    <!--
    Section principale de l'application
      * <v-main> définit le conteneur principal pour afficher le contenu de l'application
      * <router-view> est une zone de rendu dynamique utilisée par Vue Router
        pour afficher les composants des routes actuelles
    -->
    <v-main>
      <router-view />
    </v-main>
    <!--
    Pied de page de l'application
      * <v-footer> : Composant Vuetify pour un pied de page réactif et stylisé.
      * <div> : Conteneur pour le contenu du pied de page.
        - class="px-4" : Ajoute un padding horizontal (4 * 4px = 16px) pour espacer le contenu des bords.
        - class="text-center" : Centre le texte horizontalement.
        - class="w-100" : Assure que le conteneur occupe toute la largeur disponible.
    -->
    <v-footer>
      <div class="px-4 text-center w-100">2025 - Pokedex</div>
    </v-footer>
  </v-app>
</template>

<script setup>
  // Importation du composant MenuPrincipal pour l'en-tête de l'application
  import MenuPrincipal from '@/components/AppHeader.vue'
  import { usePokemonStore } from '@/stores/pokemonStore'

  // Récupération du magasin Pinia pour gérer les données des Pokémon
  const pokemonStore = usePokemonStore()

  async function chargerPokemons () {
    try {
      // On envoie une requête GET à l’API locale
      const response = await fetch('http://localhost:3535/pokemons')
      // On convertit la réponse en objet JavaScript
      const data = await response.json()
      // On affiche le résultat dans la console
      console.log('Pokémns chargés : ', data)
    } catch (error) {
      // En cas d’erreur, on affiche le message d’erreur
      console.error('Erreur lors de la récupération des Pokémon:', error)
    }
  }

  // Lorsque le composant est monté, on charge les favoris
  onMounted(() => {
    chargerPokemons()
    console.log('Chargement des favoris')
    pokemonStore.loadFavorites() // charge les favoris depuis le localStorage
  })

</script>
