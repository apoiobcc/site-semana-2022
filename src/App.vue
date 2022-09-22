<template>
  <v-app>
    <v-main>
      <v-container>
        <HeaderSemana />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import HeaderSemana from './components/HeaderSemana.vue'

export default {
  name: 'App',

  components: {
    HeaderSemana,
  },

  data: () => ({
    //
  }),
}
</script>
