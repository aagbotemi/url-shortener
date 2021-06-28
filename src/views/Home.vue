<template>
  <section>
    <v-container>
      <article class="jumbotron pb-16">
        <v-row class="mt-1 mt-md-3">
          <v-col order-md="2" md="6" cols="12">
            <img src="../assets/img/illustration-working.svg" />
          </v-col>
          <v-col order-md="1" class="jumbotron-text mt-md-16" md="6" cols="12">
            <h1>More than just shorter links</h1>
            <p class="mt-1 mt-md-3">
              Build your brand's recognition and get detailed insights on how
              your links are performing.
            </p>
            <v-btn color="#2acfcf" class="text-capitalize white--text"
            >Get Started</v-btn
            >
          </v-col>
        </v-row>
      </article>
    </v-container>
  </section>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'Home'
})
</script>
