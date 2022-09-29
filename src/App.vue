<template>
  <v-app>
    <v-main>
      <v-container>
        <HeaderSemana />
      </v-container>
    </v-main>
    <FooterSemana />
  </v-app>
</template>

<script>
import HeaderSemana from './components/HeaderSemana.vue'
import FooterSemana from './components/FooterSemana.vue'

export default {
  name: 'App',

  components: {
    HeaderSemana,
    FooterSemana,
  },

  data: () => ({
    //
  }),
}
</script>
