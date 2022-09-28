<template>
  <div class="grafo2"><img :src="require(`../assets/grafo.svg`)" height="600" /></div>
  <div class="header">
    <div class="header-top">
      <LogoHorizontal/>
      <v-tabs class="header-tab"
        background-color="white"
        center-active
      >
        <a href="#top"><v-tab>Sobre</v-tab></a>
        <a href="#calendario"><v-tab>Calendário</v-tab></a>
        <a href="#como-chegar"><v-tab>Como chegar</v-tab></a>
        <a href="#colaboradores"><v-tab>Colaboradores</v-tab></a>
      </v-tabs>
    </div>
    <div class="about">
      <p class="descricao">
        A semana da computação é uma semana de palestras que aborda diversos temas relacionados às áreas da computação. O evento é aberto a todo público e qualquer interessado pode assistir às palestras.
      </p>

      <div class="my-16">
      <p class="days">
        <span class="top">de <span class="number">24</span> a <span class="number">28</span></span> <br>de outubro de 2022
      </p>
      <p class="local">
        No auditório Jacy Monteiro, Bloco B, IME-USP.
      </p>
      </div>
    </div>
  </div>
</template>

<script>
import LogoHorizontal from './LogoHorizontal.vue'

export default {
  name: 'App',
  components: {
    LogoHorizontal
  },
  computed: {
    options () {
      return {
        duration: 300,
        offset: 0,
        easing: 'easeInOutCubic',
      }
    }
  },
}
</script>

<style scoped>
  .header {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
  }
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
    flex: 1;
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
  }
  .local {
    font-family: 'Merriweather Sans';
    color: #fffd4c;
    font-size: 18px;
    margin: 20px 0px;
  }
  .days .top {
    font-size: 36px;
  }
  .days .top .number {
    font-size: 64px;
  }
</style>
