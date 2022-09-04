<template>
  <div>
    <center>
      <strong class="small_titles_uno">Proyectos</strong>
      <v-divider style="border: solid 2px #1e88e5" width="50" />
      <br />
      <p class="small_subtitle_dos">
        Dentro de mi experiencia he tenido la oportunidad de colaborar en la creación
        páginas, sistemas y aplicaciones móviles, entre otros proyectos digitales.
      </p>

      <v-data-iterator
        :items="proyectos"
        :items-per-page.sync="itemsPerPage"
        :page.sync="page"
        hide-default-footer
      >
        <template v-slot:default="props">
          <v-row>
            <v-col
              v-for="{ index, img, nombre, fecha, tipo } in props.items"
              :key="index"
              cols="12"
              sm="6"
              md="4"
              lg="4"
            >
              <v-card
                class="mx-auto my-12"
                max-width="374"
                style="background-color: #050b1f"
                dark
              >
                <v-img
                  height="250"
                  :src="require('../../assets/image/previews/' + img)"
                ></v-img>

                <p style="padding: 10px; text-align: left">
                  {{ nombre }} / {{ fecha }} / {{ tipo }}
                </p>
              </v-card>
              <p class="title_img_galery ml-10">LOREM IPSUM DOLOR</p>
              <p class="sub_title_img_galery ml-10">
                Lorem ipsum dolor, sit amet consectetur adipisicing elit. Tenetur, nulla
                voluptas sed
              </p>
            </v-col>
          </v-row>
        </template>
      </v-data-iterator>

      <v-btn x-large icon dark color="blue darken-3" class="mr-1" @click="formerPage">
        <v-icon color="#1e88e5">mdi-chevron-left-circle</v-icon>
      </v-btn>
      <v-btn x-large icon dark color="blue darken-3" class="ml-1" @click="nextPage">
        <v-icon color="#1e88e5">mdi-chevron-right-circle</v-icon>
      </v-btn>
    </center>
  </div>
</template>

<script>
import proyectos from "../../assets/json/proyectos.json";
export default {
  data() {
    return {
      proyectos: proyectos,

      //data iterator

      itemsPerPageArray: [3, 6, , 9, 12],
      search: "",
      filter: {},
      sortDesc: false,
      page: 1,
      itemsPerPage: 3,
      sortBy: "name",
      keys: ["nombre"],
    };
  },

  computed: {
    numberOfPages() {
      return Math.ceil(this.proyectos.length / this.itemsPerPage);
    },
    filteredKeys() {
      return this.keys.filter((key) => key !== "Name");
    },
  },

  methods: {
    nextPage() {
      if (this.page + 1 <= this.numberOfPages) this.page += 1;
    },
    formerPage() {
      if (this.page - 1 >= 1) this.page -= 1;
    },
    updateItemsPerPage(number) {
      this.itemsPerPage = number;
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

.title_img_galery {
  font-size: 1rem !important;
  letter-spacing: 0.1875rem !important;
  font-weight: 700;
  line-height: 2rem;
  font-family: Work Sans, sans-serif !important;
  text-transform: uppercase !important;
  white-space: nowrap !important;
  overflow: hidden !important;
  text-overflow: ellipsis !important;
  text-align: left !important;
  margin-bottom: 16px !important;
  font-weight: 700 !important;
  color: rgba(0, 0, 0, 0.87);
}

.sub_title_img_galery {
  font-weight: 400;
  font-family: PT Sans, sans-serif !important;
  font-size: 0.9375rem !important;
  line-height: 1.5rem;
  letter-spacing: 0.03125em !important;
  text-align: left !important;
  color: #9e9e9e !important;
  caret-color: #9e9e9e !important;
}
</style>
