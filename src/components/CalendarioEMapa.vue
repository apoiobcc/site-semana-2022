<template>
  <div class="d-flex flex-column">
  <div class="calendar-sec">
    <CalendarioSemana />
  </div>
  <div class="map-sec">
    <MapaSemana />
  </div>
  </div>
</template>

<script>
import CalendarioSemana from './CalendarioSemana.vue'
import MapaSemana from './MapaSemana.vue'

export default {
  name: 'CalendarioESemana',

  components: {
    CalendarioSemana,
    MapaSemana,
  },

  data: () => ({
    //
  }),
}
</script>

<style scoped>
.calendar-sec {
  flex: 1;
}
.map-sec {
  flex: 1;
}
</style>
