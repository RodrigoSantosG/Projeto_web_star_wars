<template>
  <v-app>

    <!-- Bar -->

    <v-navigation-drawer v-model="isDrawerOpen" app temporary>
      <v-list>
        <v-list-subheader>Menu</v-list-subheader>
        <v-list-item prepend-icon="mdi-home" @click="OnView('home')">Home</v-list-item>
        <v-list-item prepend-icon="mdi mdi-death-star" @click="OnView('planetas')">Planetas</v-list-item>
      </v-list>
    </v-navigation-drawer>

    <!-- Logo -->

    <v-app-bar color="grey-4">
      <v-app-bar-nav-icon @click="isDrawerOpen = !isDrawerOpen"></v-app-bar-nav-icon>
      <v-app-bar-title class="text-h4 font-weight-bold">Star Wars</v-app-bar-title>
      <template #append>
        <v-menu>
          <template #activator="{ props }">
            <v-avatar v-bind="props">
              <v-btn icon class="mr-2">
                <v-badge dot color="info">
                  <v-icon icon="mdi-bell-outline"></v-icon>
                </v-badge>
              </v-btn>
            </v-avatar>
          </template>

          <!-- Notificacao -->

          <v-card min-width="200px">
            <v-list :Lines="false" density="compact">
              <v-list-item prepend-icon="mdi-comment-outline">
                <v-list-item-title>Comentarios</v-list-item-title>
              </v-list-item>
              <v-list-item prepend-icon="mdi-basket-outline">
                <v-list-item-title>Compra realizada</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card>
        </v-menu>

        <!-- Perfil -->

        <v-menu>
          <template #activator="{ props }">
            <v-avatar v-bind="props">
              <v-img cover src="https://cdn.dribbble.com/users/3162310/screenshots/9168149/image.gif"></v-img>
            </v-avatar>
          </template>
          <v-card min-width="200px">
            <v-list :Lines="false" density="compact">
              <v-list-item prepend-icon="mdi-account-outline">
                <v-list-item-title>Meu Perfil</v-list-item-title>
              </v-list-item>
              <v-list-item prepend-icon="mdi-heart-outline">
                <v-list-item-title>Meus favoritos</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card>
        </v-menu>
      </template>
    </v-app-bar>


    <v-main>
      <v-container>
        <home v-if="view == 'home'" />

        <planetas v-else />
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from "vue";
const isDrawerOpen = ref(false);

const view = ref("home")

const OnView = (pview) => {
  view.value = pview
};
</script>

<style>
.v-img__img--contain {
  object-fit: cover !important;
}
</style>