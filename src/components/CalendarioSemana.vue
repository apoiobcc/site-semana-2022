<template>
  <h1 id="calendario">Calendário</h1>
  <template v-if="mostrarCalendario">
  <div class="d-flex d-row calendar">
    <v-tabs
      v-model="tab"
      color="#fffd4c"
      class="days"
      direction="vertical"
      centered
      stacked
    >
      <v-tab v-for="tab in tabs" :key="tab" :value="tab"
        ><p class="number">{{ tab.day }}</p>
        <p class="weekday">{{ tab.weekday }}</p></v-tab
      >
    </v-tabs>
    <div class="content">
      <v-window v-model="tab">
        <v-window-item v-for="tab in tabs" :key="tab" :value="tab">
          <template v-for="event in tab.events" :key="event.startHour">
            <div class="d-flex flex-no-wrap align-stretch event">
              <div class="d-flex flex-no-wrap justify-center flex-column time">
                <p>
                  das
                  <span class="hour"
                    ><b>{{ event.startHour }}</b></span
                  ><br />
                  às
                  <span class="hour"
                    ><b>{{ event.endHour }}</b></span
                  >
                </p>
              </div>
              <v-card
                v-if="event.category == 'talk'"
                color="#fff"
                class="card-info"
              >
                <div class="d-flex flex-no-wrap justify-space-between">
                  <div>
                    <v-card-title class="text-h5">
                      {{ event.title }}
                    </v-card-title>

                    <v-card-subtitle>{{ event.author }}</v-card-subtitle>
                  </div>

                  <v-avatar class="ma-3" size="70" rounded="0">
                    <v-img :src="event.image"></v-img>
                  </v-avatar>
                </div>
              </v-card>
              <v-card
                v-if="event.category == 'cb'"
                color="rgba(0, 0, 0, 0.1)"
                class="d-flex align-center justify-center card-info"
                flat
              >
                <v-card-title class="text-h7 coffee-break"
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
  font-family: "Merriweather Sans";
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
  margin-right: 10px;
}
.time .hour {
  font-size: 22px;
}
.content {
  display: flex;
  flex-direction: column;
  flex: 1;
  padding-left: 10px;
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
</style>
