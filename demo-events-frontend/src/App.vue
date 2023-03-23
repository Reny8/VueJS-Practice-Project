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
      <!-- <router-view /> -->
      <p>{{ events[0].name }}</p>
      <p>{{ events[0].time }}</p>
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
    events: [{ name: "This is a test", time: new Date() }],
  }),
  // MOUNTED IS EQUIVALENT TO USEEFFECT IN REACT
  mounted: function () {
    console.log("Testing");
  },
});
</script>
