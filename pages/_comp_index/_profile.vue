<template>
  <div>
    <v-btn
      text
      color="primary"
      style="float: right"
      @click.stop="dialog = true"
      v-if="ubication == false"
    >
      Datos de contacto
    </v-btn>
    <v-btn text color="white" style="float: right" @click.stop="dialog = true" v-else>
      Luis Angel Larios Castillo
    </v-btn>

    <v-dialog v-model="dialog" max-width="400">
      <v-card class="mx-auto" max-width="400" style="background-color: orange">
        <v-img
          class="white--text align-end"
          height="230px"
          :src="require('../../assets/image/img1.jpg')"
          style="position: absolute"
        >
        </v-img>
        <center>
          <v-avatar size="200" class="mt-5 mb-1">
            <img
              src="../../assets/image/img3.jpeg"
              alt="John"
              style="border: solid 3px #f5f5f5"
            />
          </v-avatar>
        </center>
        <br />

        <div style="padding: 8px; background-color: #f5f5f5">
          <div class="text-h4" style="text-align: center" justify-content="center">
            <strong> Luis Angel Larios Castillo </strong>
          </div>

          <center>
            <strong>Ingeniero en Tecnologías de la Información</strong>
          </center>

          <div style="margin: 10px" class="text--primary">
            <div>
              <v-icon> mdi-phone </v-icon>
              (+52)748-107-56-51
            </div>

            <div>
              <v-icon> mdi-email </v-icon>
              luis44larios.99@gmail.com
            </div>
            <div>
              <v-icon> mdi-linkedin </v-icon>
              Luis Angel Larios Castillo
            </div>
            <!--  <div>
              <v-icon> mdi-map-marker </v-icon>
              Sanctórum de Lázaro Cárdenas, Tlaxcala
            </div>
            <div>
              <v-icon> mdi-home </v-icon>
              Calle: Rosales S/N, Código Postal : 90230
            </div> -->
          </div>

          <!--  <v-card-actions>
            <v-btn color="orange" text> Share </v-btn>

            <v-btn color="orange" text> Explore </v-btn>
          </v-card-actions> -->
        </div>
      </v-card>
    </v-dialog>
  </div>
</template>
<script>
export default {
  props: ["ubication"],
  data() {
    return {
      dialog: false,
    };
  },
};
</script>
