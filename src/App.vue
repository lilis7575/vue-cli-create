<template>
  <v-container>
    <v-layout>
      <v-flex xs12>
        <User/>
      </v-flex>
    </v-layout>
  </v-container>
  <!-- <v-app>
    <v-content>
      <User/>
    </v-content>
  </v-app>-->
</template>

<script>
import User from "./components/User";

export default {
  name: "App",
  components: {
    User
  }
};
</script>
