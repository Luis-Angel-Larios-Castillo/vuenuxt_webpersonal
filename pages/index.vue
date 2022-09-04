<template>
  <div style="background-color: #fafafa">
    <AboutMe />

    <ObjProfessional />

    <GaleriaProyectos />

    <ConoHabi />
  </div>
</template>

<script>
import Profile from "./_comp_index/_profile.vue";
import AboutMe from "./_comp_index/_about_me.vue";
import ObjProfessional from "./_comp_index/_obj_profeccional.vue";
import ConoHabi from "./_comp_index/_cono_habi.vue";
import GaleriaProyectos from "./_comp_index/_galeria_proyectos.vue";

export default {
  components: {
    Profile,
    AboutMe,
    ObjProfessional,
    ConoHabi,
    GaleriaProyectos,
  },
  data() {
    return {
      apt_AboutMe: true,
      apt_ObjProfessional: true,
      apt_ConoHabi: true,
      apt_GaleriaProyectos: true,
    };
  },

  methods: {},
};
</script>

<style scoped></style>
