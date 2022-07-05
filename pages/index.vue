<template>
  <div>
    <br />
    <v-tabs>
      <v-tab>Acerca de mí</v-tab>
    </v-tabs>
    <br />
    <v-row>
      <v-col>
        <v-img
          :src="require('../assets/icons/programming.png')"
          max-height="200"
          max-width="200"
        />
      </v-col>
      <v-col class="col-9">
        Ingeniero en tecnologías de la informacion con mas de un año de experiencia en el
        area de desarrollo de software, creando soluciones inovadoras con ayuda de las
        tecnologias con mayor demanda en el mercado. Obtube mi titulo en la universidad
        tecnologica de tlaxcala, logrando una formacion academica bastante enriqueceora
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
};
</script>
