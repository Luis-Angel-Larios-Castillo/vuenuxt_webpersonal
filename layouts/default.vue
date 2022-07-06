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
              alt="John"
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

    <v-parallax dark :src="require('../assets/image/img1.jpg')" style="opacity: 0.9">
      <div style="float: right">
        <v-btn style="float: right" dark icon @click="drawer = !drawer">
          <v-icon>mdi-menu</v-icon>
        </v-btn>
      </div>
      <v-row align="center" justify="center">
        <v-col class="text-center" cols="12">
          <h1 class="text-h2 mb-4 font-weight-black">
            <strong>LUIS ANGEL LARIOS CASTILLO</strong>
          </h1>
          <h4 class="text-h4 font-weight-black">
            Ingeniero en Tecnologías de la Información
          </h4>
        </v-col>
      </v-row>
    </v-parallax>

    <!--  <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" /> -->
    <!--  <v-btn icon @click.stop="miniVariant = !miniVariant">
        <v-icon>mdi-{{ `chevron-${miniVariant ? "right" : "left"}` }}</v-icon>
      </v-btn>
      <v-btn icon @click.stop="clipped = !clipped">
        <v-icon>mdi-application</v-icon>
      </v-btn>
      <v-btn icon @click.stop="fixed = !fixed">
        <v-icon>mdi-minus</v-icon>
      </v-btn>
      <v-toolbar-title v-text="title" /> -->
    <!--  <v-spacer /> -->
    <!--  <v-btn icon @click.stop="rightDrawer = !rightDrawer">
        <v-icon>mdi-menu</v-icon>
      </v-btn> -->
    <!--   </v-app-bar> -->
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <!--  <v-navigation-drawer v-model="rightDrawer" :right="right" temporary fixed>
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light> mdi-repeat </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer> -->
    <!-- <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer> -->

    <v-footer dark padless>
      <v-card flat tile class="white--text text-center" style="background-color: #154360">
        <v-card-text>
          <v-btn v-for="icon in icons" :key="icon" class="mx-4 white--text" icon>
            <v-icon size="24px">
              {{ icon }}
            </v-icon>
          </v-btn>
        </v-card-text>

        <v-card-text class="white--text pt-0">
          Phasellus feugiat arcu sapien, et iaculis ipsum elementum sit amet. Mauris
          cursus commodo interdum. Praesent ut risus eget metus luctus accumsan id
          ultrices nunc. Sed at orci sed massa consectetur dignissim a sit amet dui. Duis
          commodo vitae velit et faucibus. Morbi vehicula lacinia malesuada. Nulla
          placerat augue vel ipsum ultrices, cursus iaculis dui sollicitudin. Vestibulum
          eu ipsum vel diam elementum tempor vel ut orci. Orci varius natoque penatibus et
          magnis dis parturient montes, nascetur ridiculus mus.
        </v-card-text>

        <v-divider></v-divider>

        <v-card-text class="white--text">
          {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
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
