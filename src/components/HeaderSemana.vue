<template>
  <div :class="isMobile ? 'd-flex justify-center my-10' : 'grafo2'">
    <img :src="require(`../assets/grafo.svg`)" :height="isMobile ? 200 : 600" />
  </div>
  <div class="header" :class="!isMobile ? 'full-view' : ''">
    <v-icon v-if="isMobile" class="menu-drawer" @click.stop="drawer = !drawer" color="white">mdi-menu</v-icon>
    <v-navigation-drawer
      v-model="drawer"
      v-if="isMobile"
      absolute
      bottom
      temporary
    >
      <v-list
        nav
        dense
      >
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
          <a v-for="page in pages" :key="page" :href="page.link" class="pagelink" @click.stop="drawer = !drawer">
            <v-list-item>
              <v-list-item-title>{{ page.name }}</v-list-item-title>
            </v-list-item>
            </a>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
    <div class="d-md-flex flex-md-row ma-0 justify-space-between">
      <div :class="isMobile ? 'd-flex justify-center' : ''"><LogoHorizontal /></div>
      <v-tabs v-if="!isMobile" class="header-tab" background-color="white" center-active>
        <a v-for="page in pages" :key="page" :href="page.link"><v-tab>{{ page.name }}</v-tab></a>
      </v-tabs>
    </div>
    <div class="about d-md-flex flex-md-column justify-space-between">
      <p class="descricao my-md-12" :class="isMobile ? 'desc-mobile text-center' : ''">
        A semana da computação é uma semana de palestras que aborda diversos
        temas relacionados às áreas da computação. O evento é aberto a todo
        público e qualquer interessado pode assistir às palestras.
      </p>

      <div class="my-16 text-center text-md-left">
        <p class="days">
          <span class="top"
            >de <span class="number">24</span> a
            <span class="number">28</span></span
          >
          <br />de outubro de 2022
        </p>
        <p class="local">No auditório Jacy Monteiro, Bloco B, IME-USP.</p>
      </div>
    </div>
  </div>
</template>

<script>
import LogoHorizontal from "./LogoHorizontal.vue";

export default {
  name: "App",
  components: {
    LogoHorizontal,
  },
  computed: {
    isMobile () {
      return (window.innerWidth < 900);
    },
    options() {
      return {
        duration: 300,
        offset: 0,
        easing: "easeInOutCubic",
      };
    },
  },
  data: () => ({
    drawer: false,
    group: null,
    pages: [
      {
        name: "Sobre",
        link: "#top",
      },
      {
        name: "Calendário",
        link: "#calendario",
      },
      {
        name: "Como Chegar",
        link: "#como-chegar",
      },
      {
        name: "Colaboradores",
        link: "#colaboradores",
      },
    ],
  }),
  watch: {
    group () {
      this.drawer = false
    },
  },
};
</script>

<style scoped>
.header {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}
.menu-drawer {
  position: absolute;
  top: 20px;
}
.full-view {
  min-height: 100vh;
}
.pagelink {
  color: black !important;
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
  flex: 1;
}
.descricao {
  width: 500px;
  color: #fff;
  font-family: "Merriweather Sans";
  font-size: 1em;
}
.desc-mobile {
  width: auto;
  font-size: 1em;
  margin: 30px 10px;
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
  font-family: "Merriweather Sans";
  color: #fffd4c;
  line-height: 1.2;
  font-size: 22px;
}
.days-mobile {
  font-size: 18px;
  line-height: 1.4;
}
.local {
  font-family: "Merriweather Sans";
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
