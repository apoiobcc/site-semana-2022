<template>
  <v-app>
    <v-main>
      <v-container>
        <HeaderSemana />
      </v-container>
      <AtracoesSemana />
      <v-container>
        <CalendarioEMapa />
      </v-container>
      <FooterSemana />
    </v-main>
  </v-app>
</template>

<script>
import HeaderSemana from "./components/HeaderSemana.vue";
import AtracoesSemana from "./components/AtracoesSemana.vue";
import CalendarioEMapa from "./components/CalendarioEMapa.vue";
import FooterSemana from  "./components/FooterSemana.vue"

export default {
  name: "XIII Semana da Computação 2022",
  created() {
    document.title = "XIII Semana da Computação 2022";
  },
  components: {
    HeaderSemana,
    AtracoesSemana,
    CalendarioEMapa,
    FooterSemana,
  },

  data: () => ({
    //
  }),
};
</script>
