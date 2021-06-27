<template>
  <v-app>
    <nav-bar />
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue'
import NavBar from '@/components/NavBar.vue'

export default Vue.extend({
  name: 'App',

  components: {
    NavBar
  },
  data: () => ({
    //
  })
})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700&display=swap');

:root {
  /* Primary color */
  --clr-cyan: hsl(180, 66%, 49%);
  --clr-dark-violet: hsl(257, 27%, 26%);
  /* Secondary */
  --clr-red: hsl(0, 87%, 67%);
  /* Neutral */
  --clr-gray: hsl(0, 0%, 75%);
  --clr-grayish-violet: hsl(257, 7%, 63%);
  --clr-very-dark-blue: hsl(255, 11%, 22%);
  --clr-very-dark-violet: hsl(260, 8%, 14%);

  --font-size: 18px;
  --font-weight: 500;
  --font-weight-lg: 700;
}

body  {
  font-family: 'Poppins', sans-serif;
  font-size: 18px;
}
</style>
