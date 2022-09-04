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
      <v-btn style="float: right; margin: 10px" icon dark @click="drawer = !drawer">
        <v-icon>mdi-close</v-icon>
      </v-btn>
      <br />
      <br />
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
          <!--  <p class="font-weight-medium">Luis Angel Larios Castillo</p> -->
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

    <v-parallax dark :src="require('../assets/image/fondo4.jpg')" height="700">
      <div style="float: right">
        <v-btn style="float: right; margin: 10px" color="white" @click="drawer = !drawer">
          <!--   <v-icon>mdi-menu</v-icon> -->
          Menú
        </v-btn>
      </div>
      <v-row align="center" justify="center">
        <v-col class="text-center" cols="12">
          <h1 class="text-h1 mb-4 font-weight-black">
            <strong>Bienvenido a mi web personal</strong>
          </h1>
          <h1 class="text-h2 mb-4 font-weight-black">
            <strong>LUIS ANGEL LARIOS CASTILLO</strong>
          </h1>
          <h4 class="text-h4 font-weight-black">
            Ingeniero en Tecnologías de la Información
          </h4>
        </v-col>
      </v-row>
    </v-parallax>

    <Nuxt />

    <v-footer dark padless>
      <v-card
        flat
        tile
        class="white--text text-center col-12"
        style="background-color: #154360"
      >
        <v-card-text>
          <v-btn v-for="icon in icons" :key="icon" class="mx-4 white--text" icon>
            <v-icon size="24px">
              {{ icon }}
            </v-icon>
          </v-btn>
        </v-card-text>

        <v-card-text class="white--text pt-0">
          Luis Angel Larios Castillo - Programador Full Stack
        </v-card-text>

        <v-divider></v-divider>

        <v-card-text class="white--text">
          {{ new Date().getFullYear() }} — <strong>Copyright</strong>
        </v-card-text>
      </v-card>
    </v-footer>
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
      drawer: false,
      fixed: false,
      actualubication: true,
      items: [
        {
          icon: "mdi-home",
          title: "Principal",
          to: "/",
        },
        /*   {
          icon: "mdi-chart-bubble",
          title: "Experiencia",
          to: "/experiencia",
        }, */
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "Vuetify.js",
      icons: ["mdi-github", "mdi-linkedin", "mdi-twitter"],

      apt_AboutMe: true,
      apt_ObjProfessional: true,
      apt_ConoHabi: true,
      apt_GaleriaProyectos: true,
    };
  },
  methods: {},
};
</script>

<style scoped></style>
