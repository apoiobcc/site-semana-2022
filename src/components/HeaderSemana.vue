<template>
  <div class="grafo2"><img :src="require(`../assets/grafo.svg`)" height="600" /></div>
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
        <a href="#colaboradores"><v-tab>Colaboradores</v-tab></a>
      </v-tabs>
    </v-row>
    <v-row no-gutters class="about">
      <p class="descricao" id="sobre">
        A semana da computação é uma semana de palestras que aborda diversos temas relacionados às áreas da computação. O evento é aberto a todo público e qualquer interessado pode assistir às palestras.
      </p>

      <p class="days">
        <span class="top">de <span class="number">19</span> a <span class="number">23</span></span> <br>de outubro de 2022
      </p>
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
    margin: 0px;
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
  .about {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 550px;
  }
  .descricao {
    width: 500px;
    color: #fff;
    font-family: 'Merriweather Sans';
    font-size: 1em;
    margin: 50px 0px;
}
  .grafo2 { 
    width: 400px;
    object-fit: cover;
    position: absolute;
    top: 100px;
    right: 0;
    opacity: 70%;
    overflow: hidden;
  }
  .days {
    font-family: 'Merriweather Sans';
    color: #fffd4c;
    line-height: 1.2;
    font-size: 22px;
    margin: 20px 0px;
  }
  .days .top {
    font-size: 36px;
  }
  .days .top .number {
    font-size: 64px;
  }
</style>
