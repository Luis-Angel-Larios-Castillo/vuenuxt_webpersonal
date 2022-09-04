<template>
  <div>
    <v-list-item-title class="text-h4 mb-1"> EXPERIENCIA PROFESIONAL: </v-list-item-title>

    <template>
      <v-timeline>
        <v-timeline-item>timeline item</v-timeline-item>
        <v-timeline-item class="text-right"> timeline item </v-timeline-item>
        <v-timeline-item>timeline item</v-timeline-item>
      </v-timeline>
    </template>
  </div>

  <!-- <v-app-bar fixed app color="transparent" elevation="0">
        <v-spacer />
        <div
          class="hidden-sm-and-down"
          style="border: solid 3px #f5f5f5; background-color: none"
        >
          <v-tabs right color="#06BC9B">
            <v-tabs-slider color="#06BC9B"></v-tabs-slider>
            <v-tab v-for="(item, i) in items" :key="i" :to="item.to" router exact>{{
              item.title
            }}</v-tab>
            <v-tab icon @click="drawer = !drawer"> Menu </v-tab>
          </v-tabs>
        </div>

        <div class="hidden-md-and-up">
          <div style="float: right">
            <v-btn style="float: right" icon @click="drawer = !drawer">
              <v-icon>mdi-menu</v-icon>
            </v-btn>
          </div>
        </div>
      </v-app-bar> -->
</template>
<script>
export default {
  layout: "secundario",
};
</script>
