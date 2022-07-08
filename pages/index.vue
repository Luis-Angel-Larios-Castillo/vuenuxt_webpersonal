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
        <p class="text-h6">
          Ingeniero en tecnologías de la información con más de un año de experiencia en
          él área de desarrollo de software, creando soluciones innovadoras con las
          tecnologías con mayor demanda en el mercado, obtuve mi título en la universidad
          tecnológica de Tlaxcala, logrando una formación académica bastante enriquecedora
          en el campo de tecnologías de la información, área multimedia y comercio
          electrónico.
        </p>
        <br />

        <Profile :ubication="actualubication" />
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
        <p class="text-h6">
          Crear y diseñar páginas y sistemas web, basados en HTML5, CSS3, Java Script,
          PHP, Django y Vue.js, desarrollar aplicaciones móviles haciendo uso Android
          Studio, Ionic y React Native, analizar los modelos, requerimientos y diagramas
          UML para su desarrollo. Emplear gestores de contenido como lo es WordPress para
          la creación de sitios y blogs. Manejar herramientas de diseño de la paquetería
          de Adobe y Cinema 4D.
        </p>
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
        :items="newlistaitems"
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
              <v-select
                v-model="categoriaselected"
                flat
                solo-inverted
                hide-details
                :items="categorias"
                prepend-inner-icon="mdi-magnify"
                label="Ordenar por"
                item-text="name"
                item-value="name"
                v-on:change="filtrarCategoria()"
              ></v-select>
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
                    <p class="text-h6">{{ item.nombre }}</p>
                    <!-- <p>{{ item.categoria }}</p> -->
                    <v-btn
                      color="primary"
                      text
                      dark
                      @click="(dialogdetalles = true), (detallesitemselect = item)"
                    >
                      Ver mas
                    </v-btn>

                    <!-- {{ item.description }} -->
                  </v-col>
                </v-row>
              </div>
            </v-col>
          </v-row>
        </template>
      </v-data-iterator>
    </v-container>

    <v-dialog v-model="dialogdetalles" max-width="300">
      <v-card>
        <v-card-title class="text-h5 mb-5">
          {{ detallesitemselect.nombre }}
        </v-card-title>
        <v-card-subtitle style="text-align: justify" justify-content="center">
          <strong> Categoría: </strong> {{ detallesitemselect.categoria }}
        </v-card-subtitle>

        <v-card-subtitle style="text-align: justify" justify-content="center">
          <strong> Experiencia: </strong> {{ detallesitemselect.description }}
        </v-card-subtitle>
      </v-card>
    </v-dialog>
    <br />
    <br />
  </div>
</template>

<script>
import Profile from "./_comp_index/_profile.vue";
import conocimientos from "../assets/json/conocimientos.json";
export default {
  components: {
    Profile,
  },
  data() {
    return {
      actualubication: false,
      alert: true,
      dialogdetalles: false,
      detallesitemselect: {},
      //data iteraror

      search: "",
      filter: {},
      sortDesc: false,
      categoriaselected: "",
      newlistaitems: [],
      categorias: [
        {
          name: "Todas las categorías",
          value: "all",
        },
        {
          name: "Suite Ofimática",
          value: "office",
        },
        {
          name: "Diseño Gráfico",
          value: "disaing",
        },
        {
          name: "Desarrollo de Software",
          value: "developer",
        },
        {
          name: "Diagramas y Maquetado",
          value: "modeler",
        },
      ],
      sortBy: "categoria",
      keys: ["Nombre", "Categoria"],
      items: conocimientos,
    };
  },
  computed: {
    filteredKeys() {
      return this.keys.filter((key) => key !== "Name");
    },
  },

  created() {
    this.listacompleta();
  },
  methods: {
    listacompleta() {
      this.newlistaitems = this.items;
    },
    filtrarCategoria() {
      this.newlistaitems = [];

      if (this.categoriaselected == "Todas las categorías") {
        this.listacompleta();
      } else {
        this.items.forEach((item) => {
          if (item.categoria == this.categoriaselected) {
            this.newlistaitems.push(item);
          }
        });
      }
    },
  },
};
</script>
