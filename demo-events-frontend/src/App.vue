<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title>Events Demo Vue Project</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-data-table :headers="headers" :items="events">
        <template v-slot:items="props">
          <td>{{ props.item.name }}</td>
          <td>{{ props.item.time }}</td>
        </template>
      </v-data-table>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from "vue";
interface Event {
  name: string;
  time: Date;
}
const BACKEND_URL = "http://localhost:80";
export default Vue.extend({
  name: "App",
  // THIS IS WHERE WE CAN DEFINE ALL OF OUR REACTIVE ELEMENTS
  data: function () {
    return {
      events: [],
      headers: [
        {
          text: "Name",
          value: "name",
        },
        {
          text: "Time",
          value: "time",
        },
      ],
    };
  },
  methods: {
    getAllEvents: async function () {
      const response = await fetch(`${BACKEND_URL}/events`);
      const json = await response.json();
      json.events.forEach((item: any) => {
        item.time = new Date(item.time);
      });
      this.events = json.events;
    },
  },

  // MOUNTED IS EQUIVALENT TO USEEFFECT IN REACT
  mounted: async function () {
    this.getAllEvents();
  },
});
</script>
