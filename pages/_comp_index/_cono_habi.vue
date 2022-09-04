<template>
  <div>
    <div>
      <br />
      <br />
      <br />
      <center>
        <strong class="small_titles_uno">Concimiento y habilidades</strong>
        <v-divider style="border: solid 2px #1e88e5" width="50" />
        <br />
        <p class="small_subtitle_dos">
          A lo largo de mi experiencia profesional como desarrollador he tenido la
          oportunidad de emplear los siguientes lenguajes, framework y herramientas de
          software para brindar soluciones innovadoras.
        </p>
      </center>

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
                        :src="require('../../assets/icons/' + item.icon)"
                        max-height="120"
                        max-width="100"
                      />
                    </v-col>
                    <v-col>
                      <p class="text-h6">{{ item.nombre }}</p>

                      <!--   <v-btn
                        color="primary"
                        text
                        dark
                        @click="(dialogdetalles = true), (detallesitemselect = item)"
                      >
                        Ver mas
                      </v-btn> -->
                    </v-col>
                  </v-row>
                </div>
              </v-col>
            </v-row>
          </template>
        </v-data-iterator>
      </v-container>
    </div>

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
import conocimientos from "../../assets/json/conocimientos.json";

export default {
  data() {
    return {
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

<style scoped>
.small_titles_uno {
  font-size: 2rem !important;
  font-weight: 700;
  line-height: 2rem;
  letter-spacing: 0.1875rem !important;
  font-family: Work Sans, sans-serif !important;
  text-transform: uppercase !important;
  text-align: center !important;
  margin-bottom: 8px !important;
  font-weight: 700 !important;
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
