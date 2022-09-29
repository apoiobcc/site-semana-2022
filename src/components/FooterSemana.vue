<template>
    <v-footer>
        <v-col cols="4">
            <v-row align="center" justify="center">
                <v-col cols="10" lg="8" offset-lg="0">
                    <v-img class="ime-logo" src="@/assets/images/logoime.svg"></v-img>
                </v-col>
                <v-col cols="10" lg="8" offset-lg="0">
                    <v-img src="@/assets/images/logobcc.png"></v-img>
                </v-col>
            </v-row>
        </v-col>

        <v-col cols="8">
            <v-row justify="center"><h2 id="colaboradores">Colaboradores</h2></v-row>
            <v-row align="center" justify="center">
                <v-col cols="6" lg="4" offset-lg="0">
                    <v-img src="@/assets/images/logopoatek.png"></v-img>
                </v-col>        
                <v-col cols="6" lg="4" offset-lg="0">
                    <v-img src="@/assets/images/logoopus.png"></v-img>
                </v-col> 
            </v-row>
            <v-row align="center" justify="center">
                <v-col cols="6" lg="4" offset-lg="0">
                    <v-img src="@/assets/images/logotagimf.svg"></v-img>
                </v-col>  
            </v-row>
        </v-col>
    </v-footer>
</template>

<style scoped>
footer {
  margin: 0;
  padding: 100px;
  max-height: 25em;
  background-color: #272727;
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

