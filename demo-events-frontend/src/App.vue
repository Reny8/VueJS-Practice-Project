<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title>Events</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <template>
        <v-data-table :headers="headers" :items="events">
          <template v-slot:items="props">
            <td>{{ props.item.name }}</td>
            <td>{{ props.item.time }}</td>
          </template>
        </v-data-table></template
      >
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from "vue";
interface Event {
  name: string;
  time: Date;
}

export default Vue.extend({
  name: "App",
  // THIS IS WHERE WE CAN DEFINE ALL OF OUR REACTIVE ELEMENTS
  data: () => ({
    events: [
      { name: "This Is A Test", time: new Date() },
      { name: "Second Test", time: new Date() },
    ],
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
  }),
  // MOUNTED IS EQUIVALENT TO USEEFFECT IN REACT
  mounted: function () {
    console.log(this.events);
  },
});
</script>
