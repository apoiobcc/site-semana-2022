<template>
    <v-footer>
        <v-col cols="12" lg="3">
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
            <v-row justify="center" rows="12"><h2 id="colaboradores">Colaboradores</h2></v-row>
            <v-row align="center" justify="center" rows="12">
              <v-img src="@/assets/images/logoopus.png"></v-img>
              <v-img src="@/assets/images/logopoatek.png"></v-img>
              <v-img src="@/assets/images/logotagimf.svg"></v-img>
            </v-row>
        </v-col>
    </v-footer>
</template>

<style scoped>
footer {
  margin: 0;
  padding: 100px;
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

