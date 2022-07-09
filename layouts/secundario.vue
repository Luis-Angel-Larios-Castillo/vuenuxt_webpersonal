<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
      dark
      style="background-color: #212529"
    >
      <v-list>
        <div align="center" justify="center" class="mb-6">
          <v-avatar size="120" class="mt-5 mb-3">
            <img
              src="../assets/image/img3.jpeg"
              alt="Luis"
              style="border: solid 3px #f5f5f5"
            />
          </v-avatar>
          <br />

          <Profile :ubication="actualubication" />
        </div>
        <br />
        <v-divider></v-divider>
        <v-list-item v-for="(item, i) in items" :key="i" :to="item.to" router exact>
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
        <v-divider></v-divider>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Profile from "../pages/_comp_index/_profile.vue";
export default {
  components: {
    Profile,
  },
  data() {
    return {
      clipped: false,
      drawer: true,
      fixed: false,
      actualubication: true,
      items: [
        {
          icon: "mdi-home",
          title: "Principal",
          to: "/",
        },
        {
          icon: "mdi-chart-bubble",
          title: "Experiencia",
          to: "/experiencia",
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "Vuetify.js",
      icons: ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"],
    };
  },
};
</script>

<style scoped></style>
