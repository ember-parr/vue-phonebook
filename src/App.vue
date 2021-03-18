<template>
  <v-app>
    <v-app-bar app color="blue-grey" dark>
      <div class="d-flex align-center">
        <h3>Ember's Phonebook App</h3>
      </div>
    </v-app-bar>

    <v-main class="mt-5 mx-10">
      <phonebook />
    </v-main>
  </v-app>
</template>

<script>
import Phonebook from "./components/Phonebook"
export default {
  name: "App",

  components: {
    Phonebook
  },

  data: () => ({
    //
  })
};
</script>
