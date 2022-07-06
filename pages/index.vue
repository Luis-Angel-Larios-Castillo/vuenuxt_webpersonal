<template>
  <div>
    <br />

    <v-alert
      v-model="alert"
      dismissible
      color="cyan"
      border="left"
      elevation="2"
      colored-border
      type="info"
    >
      ¡Bienvenido a mi página web!.
    </v-alert>

    <v-list-item-title class="text-h4 mb-1"> ACERCA DE MÍ: </v-list-item-title>
    <br />
    <v-row>
      <v-col style="text-align: justify" justify-content="center">
        <v-img
          :src="require('../assets/icons/senior.png')"
          max-height="300"
          max-width="300"
        />
      </v-col>
      <v-col
        class="col-sm-12 col-lg-8 col-md-7"
        style="text-align: justify"
        justify-content="center"
      >
        <v-list-item-title class="text-h5 mb-1 bold" style="color: #154360">
          <strong><i>Datos de interés:</i></strong>
        </v-list-item-title>
        Ingeniero en tecnologías de la información con más de un año de experiencia en él
        área de desarrollo de software, creando soluciones innovadoras con las tecnologías
        con mayor demanda en el mercado, obtuve mi título en la universidad tecnológica de
        Tlaxcala, logrando una formación académica bastante enriquecedora en el campo de
        tecnologías de la información, área multimedia y comercio electrónico.
        <br />

        <Profile :ubication="actualubication" />

        <!--  <br />
        Telefono: +527481075651
        <br />
        Correo: luis44larios.99@gmail.com
        <br />
        Linkedin: luis angel larios castillo
        <br />
        facebook: Luis Angel Larios -->
      </v-col>
    </v-row>
    <br />
    <br />

    <v-list-item-title class="text-h4 mb-1" style="text-align: right">
      OBJETIVO PROFESIONAL:
    </v-list-item-title>
    <br />
    <v-row>
      <v-col
        class="col-sm-12 col-lg-8 col-md-7"
        style="text-align: justify"
        justify-content="center"
      >
        <v-list-item-title class="text-h5 mb-1 bold" style="color: #154360">
          <strong><i>Desarrollador Full Stack:</i></strong>
        </v-list-item-title>
        Crear y diseñar páginas y sistemas web, basados en HTML5, CSS3, Java Script, PHP,
        Django y Vue.js, desarrollar aplicaciones móviles haciendo uso Android Studio,
        Ionic y React Native, analizar los modelos, requerimientos y diagramas UML para su
        desarrollo. Emplear gestores de contenido como lo es WordPress para la creación de
        sitios y blogs. Manejar herramientas de diseño de la paquetería de Adobe y Cinema
        4D.
      </v-col>
      <v-col>
        <v-img
          :src="require('../assets/icons/objective.png')"
          max-height="300"
          max-width="300"
        />
      </v-col>
    </v-row>

    <br />
    <br />

    <v-list-item-title class="text-h4 mb-1">
      CONOCIMIENTOS Y HABILIDADES:
    </v-list-item-title>
    <br />

    <v-container fluid>
      <v-data-iterator
        :items="items"
        :search="search"
        :sort-by="sortBy.toLowerCase()"
        :sort-desc="sortDesc"
        :items-per-page="12"
        no-results-text="No se hallaron resultados de la búsqueda."
        no-data-text="No se tienen registros."
        :footer-props="{
          showFirstLastPage: true,
          itemsPerPageText: 'Elementos por página ',
          pageText: '{0}-{1} de {2}',
          itemsPerPageOptions: [4, 12, 24, -1],
          itemsPerPageAllText: 'Todos',
        }"
      >
        <template v-slot:header>
          <v-row>
            <v-col>
              <v-text-field
                v-model="search"
                clearable
                flat
                solo-inverted
                hide-details
                prepend-inner-icon="mdi-magnify"
                label="Buscar"
              ></v-text-field>
            </v-col>
            <v-col>
              <template v-if="$vuetify.breakpoint.mdAndUp">
                <v-select
                  v-model="sortBy"
                  flat
                  solo-inverted
                  hide-details
                  :items="keys"
                  prepend-inner-icon="mdi-magnify"
                  label="Ordenar por"
                ></v-select>
              </template>
            </v-col>
          </v-row>
        </template>

        <template v-slot:default="props">
          <v-row>
            <v-col
              v-for="item in props.items"
              :key="item.name"
              cols="12"
              sm="6"
              md="4"
              lg="3"
              class="mt-5"
            >
              <div>
                <v-row>
                  <v-col>
                    <v-img
                      :src="require('../assets/icons/' + item.icon)"
                      max-height="120"
                      max-width="100"
                    />
                  </v-col>
                  <v-col>
                    <p>{{ item.nombre }}</p>
                    <p>{{ item.categoria }}</p>

                    <!-- {{ item.description }} -->
                  </v-col>
                </v-row>
              </div>
            </v-col>
          </v-row>
        </template>
      </v-data-iterator>
    </v-container>

    <br />
    <br />
  </div>
</template>

<script>
import Profile from "./_comp_index/_profile.vue";
export default {
  components: {
    Profile,
  },
  data() {
    return {
      actualubication: false,
      alert: true,

      //data iteraror

      search: "",
      filter: {},
      sortDesc: false,

      sortBy: "categoria",
      keys: ["Nombre", "Categoria"],
      items: [
        {
          nombre: "Word",
          categoria: "Suite Ofimática",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "Power Point",
          categoria: "Suite Ofimática",
          icon: "programacion/html-5.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "Excel",
          categoria: "Suite Ofimática",
          icon: "programacion/js.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "Access",
          categoria: "Suite Ofimática",
          icon: "programacion/php.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "Publisher",
          categoria: "Suite Ofimática",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "Project",
          categoria: "Suite Ofimática",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },

        //Programas de diseño
        {
          nombre: "Photoshop",
          categoria: "Diseño Gráfico",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "Premier Pro",
          categoria: "Diseño Gráfico",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "Animate",
          categoria: "Diseño Gráfico",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "After Effects",
          categoria: "Diseño Gráfico",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "Audition",
          categoria: "Diseño Gráfico",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },

        //Programas de desarrollo de software

        {
          nombre: "PHP",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },

        {
          nombre: "Java Script",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },

        {
          nombre: "Django",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },

        {
          nombre: "Android Studio",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },

        {
          nombre: "Nuxt.js",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },

        {
          nombre: "Vue.js",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },

        {
          nombre: "Ionic",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "React",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "React Native",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },

        {
          nombre: "HTML 5",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "CSS 3",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },

        {
          nombre: "Bootstrap",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "Vuetify",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },
        {
          nombre: "Material UI",
          categoria: "Desarrollo de software",
          icon: "programacion/css-3.png",
          description: "Gestionar documentos",
        },
      ],
    };
  },
  computed: {
    filteredKeys() {
      return this.keys.filter((key) => key !== "Name");
    },
  },
  methods: {},
};
</script>
