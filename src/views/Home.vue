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
    <article class="statistics">
      <v-container>
        <v-form @submit.prevent="getUrl" class="d-sm-flex align-self-center">
          <v-text-field
            label="Shorten a link here..."
            outlined
            background-color="#fff"
            dense
            solo
            hide-details="auto"
            v-model="url"
            :rules="urlRules"
            :disabled="loading"
          ></v-text-field>
          <v-btn
            type="submit"
            color="#2acfcf"
            :loading="loading"
            class="text-capitalize white--text ml-sm-5 mt-3 mt-sm-0"
          >Shorten it</v-btn
          >
        </v-form>
        <div class="my-10">{{ shortenedUrl }}</div>
      </v-container>
    </article>
  </section>
</template>

<script lang="ts">
import Vue from 'vue'
import icons from '@/utils/icons'
import axios from 'axios'

export default Vue.extend({
  name: 'Home',
  data: () => ({
    icons,
    url: '' as string,
    valid: false as boolean,
    urlRules: [
      (url: any) => !!url || 'Url is required',
      (url: any) => /^(ftp|http|https):\/\/[^ "]+$/.test(url) || 'Input the correct url'
    ],
    loading: false as boolean,
    shortenedUrl: '' as string,
    clicked: true as boolean
  }),
  mounted () {
    this.getUrl()
  },
  methods: {
    async getUrl () {
      if (this.url) {
        this.loading = true
        await axios
          .get(`https://api.shrtco.de/v2/shorten?url=${this.url}`)
          .then((response: any) => {
            console.log(response.data)
            const res = response.data
            this.shortenedUrl = res.result.short_link
            this.url = ''
          })
          .catch((error: any) => {
            console.log(error.message)
          })
          .finally(() => {
            this.loading = false
          })
      }
    }
  }
})
</script>

<style scoped lang="scss">
.jumbotron {
  margin: 0 1rem;

  .jumbotron-text {
    h1 {
      font-size: 35px;
      line-height: 1;
      color: var(--clr-very-dark-blue);
    }
    p {
      font-size: 18px;
      line-height: 1.4;
      color: var(--clr-grayish-violet);
    }
  }
}

.statistics {
  background: var(--clr-gray);

  form {
    transform: translateY(-45px);
    background: url("../assets/img/bg-shorten-mobile.svg"), var(--clr-dark-violet);
    //background: var(--clr-dark-violet);
    border-radius: 10px;
    padding: 1.2rem 1.2rem;
    margin: 0rem 1rem;

    button {
     // width: 100%;
    }
  }
}
@media only screen and (max-width: 575px) {
  .statistics {
    form {
      button {
        width: 100%;
      }
    }
  }
}
@media only screen and (min-width: 767.5px) {
  .jumbotron {
    .jumbotron-text {
      h1 {
        font-size: 60px;
      }
    }
  }
  .statistics {
    form {
      padding: 1.2rem 1rem;
      background: url("../assets/img/bg-shorten-desktop.svg"), var(--clr-dark-violet);
      //background: var(--clr-dark-violet);

    }
  }
}
</style>
