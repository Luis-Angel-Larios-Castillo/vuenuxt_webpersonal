<template>
  <div>
    <br />
    <br />
    <div style="background-color: #050b1f; padding: 20px">
      <v-list-item-title class="text-h4 mb-1" style="text-align: right; color: #fff">
        OBJETIVO PROFESIONAL
      </v-list-item-title>
      <br />
      <v-row>
        <v-col
          class="col-sm-12 col-lg-8 col-md-7"
          style="text-align: justify"
          justify-content="center"
        >
          <v-list-item-title class="text-h5 mb-5 bold" style="color: #fff">
            <strong><i>Desarrollador Full Stack:</i></strong>
          </v-list-item-title>

          <p class="text-h6" style="color: #f5f5f5">
            Crear y diseñar páginas y sistemas web, basados en HTML5, CSS3, Java Script,
            PHP, Django y Vue.js, desarrollar aplicaciones móviles haciendo uso Android
            Studio, Ionic y React Native, analizar los modelos, requerimientos y diagramas
            UML para su desarrollo. Emplear gestores de contenido como lo es WordPress
            para la creación de sitios y blogs. Manejar herramientas de diseño de la
            paquetería de Adobe y Cinema 4D.
          </p>
        </v-col>
        <v-col>
          <center>
            <v-img
              :src="require('../../assets/icons/icondev.png')"
              max-height="300"
              max-width="300"
            />
          </center>
        </v-col>
      </v-row>
    </div>
    <br />
    <br />
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
};
</script>

<style scoped></style>
