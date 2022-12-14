<template>
<h1 class="text-center text-md-left" id="calendario">Calendário</h1>
  <template v-if="mostrarCalendario">
  <div class="d-flex flex-column flex-md-row calendar">
    <v-tabs
      v-model="tab"
      color="#fffd4c"
      class="days"
      :direction="calendarDirection"
      centered
      stacked
    >
      <v-tab v-for="tab in tabs" :key="tab" :value="tab"
        ><p class="number text-subtitle-2 text-md-h6 text-weight-bold">{{ tab.day }}</p>
        <p class="weekday">{{ isMobile ? tab.weekday.substr(0, 3) + '.' : tab.weekday }}</p></v-tab
      >
    </v-tabs>
    <div class="content pl-md-2 pt-2 pt-md-0">
      <v-window v-model="tab">
        <v-window-item v-for="tab in tabs" :key="tab" :value="tab">
          <template v-for="event in tab.events" :key="event.startHour">
            <div class="d-flex flex-column flex-md-row flex-no-wrap align-stretch event">
              <div class="d-flex flex-no-wrap justify-center flex-row flex-md-column mr-md-2 time">
                  <span>
                    das
                    <span class="hour"
                      ><b>{{ event.startHour }}</b></span
                    > 
                  </span>
                  <span>
                  às
                  <span class="hour"
                    ><b>{{ event.endHour }}</b></span
                  >
                  </span>
              </div>
              <v-card
                v-if="event.category == 'talk'"
                color="#fff"
                :rounded="isMobile ? 0 : 3"
                class="card-info pa-3 rounded-b"
              >
                <div class="d-flex justify-space-between">
                  <div>
                    <v-card-title class="text-h6 text-md-h5 text-wrap">
                      {{ event.title }}
                    </v-card-title>

                    <v-card-subtitle class="author text-wrap">{{ event.author }}</v-card-subtitle>
                  </div>

                  <v-avatar class="ma-3" size="70" rounded="3">
                    <v-img :src="event.image"></v-img>
                  </v-avatar>
                </div>
              </v-card>
              <v-card
                v-if="event.category == 'cb'"
                color="rgba(0, 0, 0, 0.1)"
                class="d-flex align-center justify-center rounded-b card-info"
                :rounded="isMobile ? 0 : 3"
                flat
              >
                <v-card-title class="pa-8 pa-md-6 text-h7 coffee-break"
                  ><v-icon>mdi-coffee</v-icon
                  ><span class="px-4">{{ event.title }}</span></v-card-title
                >
              </v-card>
            </div>
          </template>
        </v-window-item>
      </v-window>
    </div>
  </div>
  </template>
  <template v-else>
    <div class="block-box">
      <v-icon size="100">mdi-lock</v-icon>
      <span class="block-text"><h2>O calendário ainda não está disponível :(</h2></span>
    </div>
  </template>
</template>

<script>
export default {
  props: {
    mostrarCalendario: {
      type: Boolean,
      default: false,
    },
  },
  data: () => ({
    info: null,
    tab: null,
    isMobile: false,
    tabs: [
      {
        day: "24/10",
        weekday: "segunda",
        events: [],
      },
      {
        day: "25/10",
        weekday: "terça",
        events: [],
      },
      {
        day: "26/10",
        weekday: "quarta",
        events: [],
      },
      {
        day: "27/10",
        weekday: "quinta",
        events: [],
      },
      {
        day: "28/08",
        weekday: "sexta",
        events: [],
      },
    ],
  }),
  beforeMount () {
    this.isMobile = (window.innerWidth < 900);
  },
  computed: {
    calendarDirection () {
      if (!this.isMobile) {
        return 'vertical'
      } else {
        return 'horizontal'
      }
    }
  },
  async mounted() {
    const response = await fetch(
      "https://sheets.googleapis.com/v4/spreadsheets/1UlwfoFlbhlgoWafuOMFSMgT7OgsIizjljvDIgrVUTOc/values/Sheet1?key=" +
        process.env.VUE_APP_GOOGLE_API_SHEETS_KEY
    );
    const data = await response.json();
    this.info = data;

    const events = data.values.slice(1);
    for (let i = 0; i < events.length; i++) {
      const event_obj = {
        category: events[i][6],
        title: events[i][0],
        author: events[i][1],
        startHour: events[i][3],
        endHour: events[i][4],
        image: events[i][5],
      };

      let day = events[i][2];

      for (let j = 0; j < this.tabs.length; j++) {
        if (this.tabs[j].day.substring(0, 2) == day) {
          this.tabs[j].events.push(event_obj);
        }
      }
    }
  },
};
</script>

<style scoped>
h1 {
  margin: 20px 0px;
  font-family: "Merriweather Sans" !important;
  color: #fffd4c;
}
.calendar {
  width: 100%;
  margin: 10px 0px;
}
.days {
  color: #fff;
}
.time {
  color: #fff;
  background-color: rgba(255, 253, 76, 0.1);
  color: #fffd4c;
  border-left: 2px solid #fffd4c;
  font-size: 12px;
  padding: 10px 20px;
}
.time .hour {
  font-size: 22px;
}
.content {
  display: flex;
  flex-direction: column;
  flex: 1;
}
.number {
  font-size: 22px;
}
.weekday {
  font-size: 12px;
}
.event {
  margin-bottom: 10px;
}
.card-info {
  flex: 1;
}
.coffee-break {
  color: #fffd4c;
}
.block-box {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  color: #fffd4c;
  font-family: "Merriweather Sans";
}
.block-text {
  max-width: 300px;
  text-align: center;
  margin: 20px 0px;
}
.author {
  margin-bottom: 20px;
}
</style>
