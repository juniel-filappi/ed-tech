<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <h2 class="pa-2">Módulo Acadêmico</h2>
      <router-link
        to="/dashboard"
        class="pa-2 d-flex justify-space-between bg-orange"
      >
        <v-icon>mdi-account-group</v-icon>
        <h3 class="text-white">Alunos</h3>
        <div></div>
      </router-link>
    </v-navigation-drawer>

    <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          :src="logo"
          transition="scale-transition"
          width="100"
        ></v-img>
      </v-toolbar-title>

      <template #append>
        <v-btn @click="logout">
          <v-icon>mdi-logout</v-icon>
        </v-btn>
      </template>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Logo from "@/assets/logo_growdev.svg"
import Students from "@/pages/Students/Students.vue"

export default {
  name: "Dashboard",
  components: {
    Students,
  },
  data() {
    return {
      drawer: true,
      logo: Logo,
    };
  },
  methods: {
    logout() {
      localStorage.removeItem("token");
      localStorage.removeItem("user");
      this.$router.push({ name: "Login" });
    },
  },
}
</script>

<style scoped>
a {
  color: inherit;
  text-decoration: none;
}
</style>
