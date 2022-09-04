<template>
  <div>
    <br />
    <br />
    <center>
      <v-avatar size="70" class="mt-5 mb-3">
        <img
          src="../../assets/icons/programming.png"
          alt="Luis"
          style="border: solid 3px #f5f5f5"
        />
      </v-avatar>
      <br />

      <strong class="title_principal_seccion">ACERCA DE MÍ</strong>
      <v-divider style="border: solid 2px #1e88e5" width="50" />
      <br />

      <p class="small_subtitle_dos col-9">
        Programador full stack con más de dos años de experiencia en el desarrollo de
        sitios y sistemas web. A lo largo de estos años, he tenido el privilegio de formar
        parte en la creación de grandes retos para una empresa internacional como lo es
        Motherson Group y Pixsoft una empresa de nivel regional, las cuales han
        contribuido en gran medida a mis conocimientos como desarrollador.
      </p>
    </center>
    <br />

    <v-row>
      <v-col class="col-sm-12 col-lg-4 col-md-4">
        <center>
          <v-btn
            class="mx-3"
            fab
            dark
            x-large
            color="#42a5f6"
            v-if="btnselect == 1"
            @click="btnselect = 1"
          >
            <v-icon dark>mdi-code-json</v-icon>
          </v-btn>

          <v-btn
            class="mx-3"
            fab
            outlined
            x-large
            color="#000"
            v-else
            @click="btnselect = 1"
          >
            <v-icon color="rgba(0,0,0,.54)">mdi-code-json</v-icon>
          </v-btn>
          <br />
          <br />
          <strong class="title_btn_about_me">EXPERIENCIA PROFESIONAL</strong>
          <br />
          <br />
          <v-divider width="300px"></v-divider>

          <v-btn
            class="mx-3 mt-10"
            fab
            x-large
            dark
            color="#42a5f6"
            v-if="btnselect == 2"
            @click="btnselect = 2"
          >
            <v-icon>mdi-account-circle</v-icon>
          </v-btn>

          <v-btn
            class="mx-3 mt-10"
            fab
            x-large
            outlined
            color="#000"
            v-else
            @click="btnselect = 2"
          >
            <v-icon color="rgba(0,0,0,.54)">mdi-account-circle</v-icon>
          </v-btn>

          <br /><br />
          <strong class="title_btn_about_me">DATOS DE CONTACTO</strong>

          <br />
          <br />
          <v-divider width="300px"></v-divider>
          <v-btn
            class="mx-3 mt-10"
            fab
            dark
            x-large
            color="#42a5f6"
            @click="btnselect = 3"
            v-if="btnselect == 3"
          >
            <v-icon dark>mdi-card-account-details-star </v-icon>
          </v-btn>

          <v-btn
            class="mx-3 mt-10"
            fab
            outlined
            x-large
            v-else
            color="#000"
            @click="btnselect = 3"
          >
            <v-icon color="rgba(0,0,0,.54)">mdi-card-account-details-star </v-icon>
          </v-btn>
          <br />
          <br />
          <strong class="title_btn_about_me">FORMACIÓN ACADEMICA</strong>
        </center>
      </v-col>
      <v-divider vertical></v-divider>

      <v-col class="col-sm-12 col-lg-7 col-md-7">
        <div style="margin: 10px" class="text--primary ml-10" v-show="btnselect == 2">
          <strong class="title_btn_apartdo_select">DATOS DE CONTACTO</strong>
          <br />
          <br />

          <div v-for="{ label, value, icon, url, index } in datoscontacto" :key="index">
            <v-row>
              <v-col cols="8">
                <v-text-field
                  :prepend-icon="icon"
                  :label="label"
                  :value="value"
                  outlined
                  dense
                  readonly
                  filled
                ></v-text-field>
              </v-col>

              <v-col cols="2" v-if="url">
                <v-tooltip bottom>
                  <template v-slot:activator="{ on, attrs }">
                    <v-btn
                      icon
                      color="orange accent-4"
                      dark
                      :href="url"
                      target="_blank"
                      v-bind="attrs"
                      v-on="on"
                    >
                      <v-icon dark>mdi-chevron-right-circle</v-icon>
                    </v-btn>
                  </template>
                  <span>Visitar</span>
                </v-tooltip>
              </v-col>
            </v-row>
          </div>
          <v-btn
            color="orange accent-4"
            dark
            href="/pdf/Luis_Angel_Larios_Castillo.pdf"
            target="_blank"
          >
            CV
          </v-btn>
        </div>
        <div v-show="btnselect == 1" style="margin: 10px" class="text--primary ml-10">
          <strong class="title_btn_apartdo_select">EXPERIENCIA</strong>
          <br />
          <strong class="subtitle_btn_apartado_select"> PROFESIONAL</strong>
          <br />
          <br />
          <p class="parrafo_info_btn_select">
            Programador full stack con mas de dos años de experiencia en desarrollo de
            aplicaciones móviles y sistemas web. En mi puesto actual como programador
            dentro de la empresa Pixsoft, he colaborado en 3 sistemas web y una aplicacion
            móvil.
            <br />
            <br />
            En los cuales he aquirido experiencia y conocimientos en framework de
            javascript como Vue y React, ademas de bases de datos relacionales como mysql
            y postgresql y no relacionales como firebase. Asi mismo he adquirido
            experiencia en cloud functions y servicios REST API.
          </p>
        </div>
        <div v-show="btnselect == 3" style="margin: 10px" class="text--primary ml-10">
          <strong class="title_btn_apartdo_select">FORMACIÓN</strong>
          <br />
          <strong class="subtitle_btn_apartado_select"> ACADÉMICA</strong>
          <br />
          <br />
          <p class="parrafo_info_btn_select">
            Obtuve mi título en la universidad tecnológica de Tlaxcala, logrando una
            formación académica bastante enriquecedora en el campo de tecnologías de la
            información, área multimedia y comercio electrónico. Universidad Tecnológica
            de Tlaxcala. Ingeniería en Tecnologías de la Información (2019 - 2021).
            Técnico Superior Universitario en Tecnologías de la información y comunicación
            área multimedia y comercio electrónico (2017- 2019).
          </p>
        </div>

        <div style="float: right">
          <v-btn
            class="mx-3 mt-10"
            x-large
            icon
            v-show="btnselect >= 2"
            color="#1e88e5"
            @click="restaruno()"
          >
            <v-icon color="#1e88e5">mdi-arrow-left-circle</v-icon>
          </v-btn>

          <v-btn
            class="mx-3 mt-10"
            x-large
            icon
            v-show="btnselect <= 2"
            color="#1e88e5"
            @click="sumaruno()"
          >
            <v-icon color="#1e88e5">mdi-arrow-right-circle</v-icon>
          </v-btn>
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      btnselect: 2,

      datoscontacto: [
        {
          id: 1,
          label: "Correo",
          value: "luis44larios.99@gmail.com",
          icon: "mdi-email",
        },
        {
          id: 2,
          label: "Telefono",
          value: "(+52) 748-107-56-51",
          icon: "mdi-phone",
        },
        {
          id: 3,
          label: "Linkedin",
          value: "Luis Angel Larios Castillo",
          icon: "mdi-linkedin",
          url: "https://www.linkedin.com/in/luis-angel-larios-castillo-259602210/",
        },
        {
          id: 4,
          label: "GitHub",
          value: "Luis Angel Larios",
          icon: "mdi-github",
          url: "https://github.com/Luis-Angel-Larios-Castillo?tab=repositories",
        },
        {
          id: 5,
          label: "Web Personal",
          value: "https://luis-angel-larios-castillo.github.io/",
          icon: "mdi-web",
          url: "https://luis-angel-larios-castillo.github.io/",
        },
      ],
    };
  },

  methods: {
    sumaruno() {
      this.btnselect++;
    },
    restaruno() {
      this.btnselect--;
    },
  },
};
</script>

<style scoped>
/* Probado y listo */
.title_btn_about_me {
  color: #000;
  font-weight: 700;
  letter-spacing: 2px;
  font-family: Work Sans, sans-serif;
}
/* Probado y listo */
.title_principal_seccion {
  font-size: 2rem;
  font-weight: 700;
  line-height: 2rem;
  letter-spacing: 0.1875rem;
  font-family: Work Sans, sans-serif;
  text-transform: uppercase;
  text-align: center;
  margin-bottom: 8px;
  font-weight: 700;
}
/* probado y listo */
.title_btn_apartdo_select {
  color: #000;
  letter-spacing: 1px;
  font-size: 30px;
  font-family: Work Sans, sans-serif;
}
/*probado y listo */
.subtitle_btn_apartado_select {
  color: #42a5f6;
  font-weight: 700;
  letter-spacing: 2px;
  font-family: Work Sans, sans-serif;
}

.parrafo_info_btn_select {
  text-align: justify;
  color: #757575;
  caret-color: #757575;
  font-weight: 400;
  font-family: PT Sans, sans-serif;
  font-size: 1rem;
  line-height: 1.5rem;
  letter-spacing: 0.03125em;
}

.small_subtitles_uno {
  color: #42a5f6;
  font-weight: 700;
  letter-spacing: 2px;
  font-family: Work Sans, sans-serif;
}

.small_subtitle_dos {
  color: #757575 !important;
  caret-color: #757575 !important;
  font-weight: 400;
  font-family: PT Sans, sans-serif !important;
  font-size: 0.9375rem !important;
  line-height: 1.5rem;
  letter-spacing: 0.03125em !important;
  text-align: center !important;
}
</style>
