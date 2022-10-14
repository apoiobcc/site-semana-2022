<template>
    <v-footer>
        <v-col cols="12" lg="4">
            <v-row align="center" justify="center">
                <v-col cols="12" lg="8" offset-lg="0">
                    <v-img class="ime-logo" src="@/assets/images/logoime.svg"></v-img>
                </v-col>
                <v-col cols="12" lg="8" offset-lg="0">
                    <v-img src="@/assets/images/logobcc.png"></v-img>
                </v-col>
            </v-row>
        </v-col>

        <v-col cols="12" lg="6">
          <v-row justify="center"><h2 id="colaboradores">Colaboradores</h2></v-row>
          <v-row justify="center" class="pa-16">
            <v-col v-for="partner in partners" :key="partner.name" cols="6" class="d-flex">
              <v-img :src="partner.img" :alt="partner.name"></v-img>
            </v-col>
          </v-row>
        </v-col>
    </v-footer>
</template>

<script>
  export default {
    data: () => ({
      partners: [
        {
          name: "Opus",
          img: require("@/assets/images/logoopus.png"),
        },
        {
          name: "Poatek",
          img: require("@/assets/images/logopoatek.png"),
        },
        {
          name: "TagIMF",
          img: require("@/assets/images/logotagimf.svg"),
        },
        {
          name: "Elo7",
          img: require("@/assets/images/logoelo7.svg"),
        }
      ],
    }),
  }
</script>

<style scoped>
footer {
  margin: 0;
  padding: 40px 100px;
  justify-content: space-between;
  background-color: #272727;
}
.colaborators {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 20px;
}
.partners{
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  gap: 10;
  width: 100%;
}
h2 {
  color: #fff;
  font-family: 'Merriweather Sans';
  margin: 20px 0px;
}

.ime-logo {
  -webkit-filter: invert(100%); /* safari 6.0 - 9.0 */
          filter: invert(100%);
}
</style>

