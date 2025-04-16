<template>
  <!-- Conteneur principal pour structurer la disposition de la page -->
  <v-container>
    <!--
    Titre de la page
      * mb-6 permet d'ajouter une Marge en Bas de 6 unités
      * text-center permet de centrer le texte
    -->
    <h1 class="mb-6 text-center">
      Pokédex
    </h1>

    <v-row>
      <v-col
        v-for="i in 20"
        cols="12"
        lg="3"
        md="4"
        mx="12"
        sm="6"
        xxl="2"
      >
        Mon pokémon - {{ i }}
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
// Vos scripts ou imports ici
</script>
