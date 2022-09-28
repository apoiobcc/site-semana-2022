<template>
  <v-row class="bar">
    <template v-for="(item, index) in cards" :key="index">
      <div class="card">
        <div class="icon">
          <v-icon>
            {{ item.icon }}
          </v-icon>
        </div>
        <h3>
          {{ item.title }}
        </h3>
        <p class="desc">{{ item.desc }}</p>
      </div>
      <div v-if="index < cards.length - 1" class="vert-divider"></div>
    </template>
  </v-row>
</template>

<script>
export default {
  data: () => ({
    cards: [
      {
        icon: "mdi-coffee",
        title: "COFFEE BREAKS",
        desc: "A cada intervalo dos dias da semana serão oferecidos coffee breaks aos participantes!",
      },
      {
        icon: "mdi-account",
        title: "PALESTRAS",
        desc: "Diversas empresas, grupos de pesquisa e nomes renomados da computação promoverão palestras.",
      },
      {
        icon: "mdi-forum",
        title: "INTEGRAÇÃO",
        desc: "Entre em contato com empresas e pesquisadores dos mais variados ramos da computação.",
      },
    ],
  }),
};
</script>

<style scoped>
.bar {
  background-color: #272727;
  padding: 30px 40px;
  font-family: Merriweather Sans;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.card {
  width: 230px;
  margin: 10px 30px;
}

.icon {
  font-size: 28px;
  text-align: center;
  color: #fff;
}

h3 {
  font-weight: bold;
  text-align: center;
  padding: 15px 0px;
  color: #fff;
}

.desc {
  color: #fff;
  font-size: 12px;
  text-align: center;
}

.vert-divider {
  height: 120px;
  width: 1px;
  background-image: linear-gradient(
    rgba(0, 0, 0, 0),
    rgba(255, 255, 255, 1),
    rgba(0, 0, 0, 0)
  );
}

.v-card--reveal {
  bottom: 0;
  opacity: 1 !important;
  position: absolute;
  width: 100%;
}
</style>
