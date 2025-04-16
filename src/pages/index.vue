<template>
  <v-container>
    <h1 class="mb-6 text-center">Pokédex</h1>

    <v-text-field
      clearable
      label="Rechercher un Pokémon"
      prepend-icon="mdi-magnify"
    />

    <v-row>
      <!-- Exemple de colonne vide (à dupliquer plus tard avec du contenu) -->
      <v-col
        v-for="i in 20"
        cols="12"
        lg="3"
        md="4"
        sm="6"
        xl="2"
      >
        <v-card>
          <v-img
            cover
            height="200px"
            src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
          />

          <v-card-title>
            Pokémont {{ i }}
          </v-card-title>

          <v-card-subtitle>
            Niveau: {{ i }}
          </v-card-subtitle>

          <v-card-actions>
            <v-btn
              color="red"
              icon="mdi-heart-outline"
            />
          </v-card-actions>

          <v-expand-transition>
            <div v-show="show">
              <v-divider />

              <v-card-text>
                I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to escape.
              </v-card-text>
            </div>
          </v-expand-transition>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
