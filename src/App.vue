<template>
  <v-app>
    <v-app-bar
      app
      color="pink"
      dark
    >
      <div class="d-flex align-center">
        <router-link to="/" style="color:white;text-decoration:none;">MUSIC SEARCH</router-link>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        text
        to="/"
      >
        <span class="mr-2">Home</span>
      </v-btn>
    </v-app-bar>

    <v-content>
      <router-view/>
    </v-content>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  components: {
  },

  data: () => ({
    //
  }),
};
</script>
