<template>
  <v-container class="header">
    <v-row class="header-top">
      <LogoHorizontal/>
      <v-tabs class="header-tab"
        background-color="white"
        center-active
      >
        <a href="#sobre"><v-tab>Sobre</v-tab></a>
        <a href="#calendario"><v-tab>Calendário</v-tab></a>
        <a href="#como-chegar"><v-tab>Como chegar</v-tab></a>
        <a href="#Colaboradores"><v-tab>Colaboradores</v-tab></a>
      </v-tabs>
    </v-row>
    <v-row no-gutters class="descricao">
      Semana de palestras que abordam temas variados sobre as diversas áreas da computação. O evento é aberto e qualquer interessado pode assistir as palestras.
    </v-row>
  </v-container>
</template>

<script>
import LogoHorizontal from './LogoHorizontal.vue'

export default {
  name: 'App',
  components: {
    LogoHorizontal
  }
}
</script>

<style scoped>
  .header-top {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
  a {
    text-decoration: none;
    color: #fff;
  }
  .header-tab {
    color: #fff;
  }
  .header-nav {
    display: flex;
    flex-direction: row;
    justify-content: center;
	}
  .descricao {
    width: 500px;
    margin: auto;
    padding: 0.5rem;
    text-align: justify;
    font-family: 'Merriweather';
    font-size: 1rem;
}
</style>
