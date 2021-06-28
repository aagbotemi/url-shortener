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
        <v-form
          ref="form" @submit.prevent="getUrl"
          class="d-sm-flex align-sm-center">
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
        <div
          v-if="shortenedUrl"
          class="d-flex mb-10 mt-n9 mx-4 py-2 px-7 rounded"
          style="background-color: white"
        >
          <v-spacer />
          {{ shortenedUrl }}
          <v-btn
            v-clipboard:copy="shortenedUrl"
            :disabled="loading"
            small color="#2acfcf"
            class="white--text text-capitalize ml-5"
            @click="clickedUrl"
          >{{ clicked ? 'Copied' : 'Copy'}}</v-btn>
        </div>
        <div class="advance-statistic text-center">
          <h2>Advanced Statistics</h2>
          <p>
            Track how your links are performing across the web with our advanced
            statistics dashboard.
          </p>
        </div>
        <div class="statistics-card pt-10">
          <div class="card-line"></div>
          <div class="card-line-horizontal"></div>
          <v-row class="mb-10">
            <v-col cols="12" sm="6" md="4">
              <v-card class="card mb-8 text-center text-sm-left">
                <div class="card-img pa-2 text-center">
                  <img
                    class="pt-1"
                    src="../assets/img/icon-brand-recognition.svg"
                  />
                </div>
                <h4 class="pt-0 pb-2 ml-4">Brand Recognition</h4>
                <v-card-text class="pt-0">
                  Boost your brand recognition with each click. Generic links
                  don't mean a thing. Branded links help instill confidence in
                  your content.
                </v-card-text>
              </v-card>
            </v-col>
            <v-col cols="12" sm="6" md="4">
              <v-card class="card mb-8 mt-md-6 text-center text-sm-left">
                <div class="card-img pa-2 text-center">
                  <img
                    class="pt-1"
                    src="../assets/img/icon-detailed-records.svg"
                  />
                </div>
                <h4 class="pt-0 pb-2 ml-4">Detailed Records</h4>
                <v-card-text class="pt-0">
                  Gain insights into who is clicking your links. Knowing when
                  and where people engage with your content helps inform better
                  decisions.
                </v-card-text>
              </v-card>
            </v-col>
            <v-col cols="12" sm="6" md="4">
              <v-card class="card mt-md-13 text-center text-sm-left">
                <div class="card-img pa-2 text-center">
                  <img
                    class="pt-1"
                    src="../assets/img/icon-fully-customizable.svg"
                  />
                </div>
                <h4 class="pt-0 pb-2 ml-4">Fully Customizable</h4>
                <v-card-text class="pt-0">
                  Improve brand awareness and content discoverability through
                  customizable links, supercharging audience engagement.
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </div>
      </v-container>
    </article>
    <article class="boost-link pt-16 pb-10 text-center">
      <h2 class="white--text">Boost your links today</h2>
      <v-btn
        color="#2acfcf"
        class="mt-7 text-center text-capitalize white--text"
      >Get Started</v-btn>
    </article>
    <footer>
      <v-container>
        <v-row class="py-10 mx-1">
          <v-col class="text-center text-md-left" cols="12" md="3">
            <img alt="shortly logo" class="logo" src="../assets/img/logo.svg" />
          </v-col>
          <v-col cols="12" md="9" class="text-center text-sm-left">
            <v-row>
              <v-col sm="6" md="3" cols="12">
                <h4 class="mb-1">Features</h4>
                <ul class="ml-n6">
                  <li class="mb-1">
                    <router-link class="text-decoration-none" to="/">
                      Link Shortening
                    </router-link>
                  </li>
                  <li class="mb-1">
                    <router-link class="text-decoration-none" to="/">
                      Branded Links
                    </router-link>
                  </li>
                  <li class="mb-1">
                    <router-link class="text-decoration-none" to="/">
                      Analytics
                    </router-link>
                  </li>
                </ul>
              </v-col>
              <v-col sm="6" md="3" cols="12">
                <h4 class="mb-1">Resources</h4>
                <ul class="ml-n6">
                  <li class="mb-1">
                    <router-link class="text-decoration-none" to="/">
                      Blog
                    </router-link>
                  </li>
                  <li class="mb-1">
                    <router-link class="text-decoration-none" to="/">
                      Developers
                    </router-link>
                  </li>
                  <li class="mb-1">
                    <router-link class="text-decoration-none" to="/">
                      Support
                    </router-link>
                  </li>
                </ul>
              </v-col>
              <v-col sm="6" md="2" cols="12">
                <h4>Company</h4>
                <ul class="ml-n6">
                  <li class="mb-1">
                    <router-link class="text-decoration-none" to="/">
                      About
                    </router-link>
                  </li>
                  <li class="mb-1">
                    <router-link class="text-decoration-none" to="/">
                      Our Team
                    </router-link>
                  </li>
                  <li class="mb-1">
                    <router-link class="text-decoration-none" to="/">
                      Careers
                    </router-link>
                  </li>
                  <li class="mb-1">
                    <router-link class="text-decoration-none" to="/">
                      Contact
                    </router-link>
                  </li>
                </ul>
              </v-col>
              <v-col sm="6" md="4" cols="12">
                <a class="mr-4" href="#"
                ><v-icon medium>{{ icons.facebook }}</v-icon></a
                >
                <a class="mr-4" href="#"
                ><v-icon medium>{{ icons.twitter }}</v-icon></a
                >
                <a class="mr-4" href="#"
                ><v-icon medium>{{ icons.pinterest }}</v-icon></a
                >
                <a class="mr-4" href="#"
                ><v-icon medium>{{ icons.instagram }}</v-icon></a
                >
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-container>
      <div class="copyright text-center py-1">
        <v-container>
          {{ new Date().getFullYear() }} Copyright reserved
        </v-container>
      </div>
    </footer>
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
    loading: false as boolean,
    url: '' as string,
    shortenedUrl: '' as string,
    clicked: true as boolean,
    urlRules: [
      (url: any) => !!url || 'Url is required',
      (url: any) => /^(ftp|http|https):\/\/[^ "]+$/.test(url) || 'Input the correct url'
    ]
  }),
  mounted () {
    this.getUrl()
  },
  methods: {
    clickedUrl () {
      setTimeout(() => {
        this.clicked = false
      }, 1000)

      this.clicked = true
    },
    async getUrl () {
      if (this.url) {
        this.loading = true as boolean
        await axios
          .get(`https://api.shrtco.de/v2/shorten?url=${this.url}`)
          .then((response: any) => {
            const res = response.data
            this.shortenedUrl = res.result.short_link
            this.url = ''
          })
          .catch((error: any) => {
            console.log(error.message)
          })
          .finally(() => {
            this.loading = false as boolean
            this.$refs.form.reset()
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
    border-radius: 10px;
    padding: 1.2rem 1.2rem;
    margin: 0rem 1rem;
  }

  .advance-statistic {
    max-width: 30rem;
    margin: 0 1rem;
    h2 {
      color: var(--clr-grayish-blue);
      font-size: 33px;
    }
    p {
      font-size: 18px;
      line-height: 1.4;
      color: var(--clr-grayish-violet);
    }
  }
  .statistics-card {
    margin: 1.2rem 1rem;
    position: relative;

    .card {
      .card-img {
        transform: translateY(-25px);
        width: 3.5rem;
        height: 3.5rem;
        border-radius: 50%;
        background-color: hsl(257, 27%, 26%);
        margin: 0 auto;

        img {
          width: 1.8rem;
        }
      }
    }
    .card-line-horizontal {
      position: absolute;
      left: 49.6%;
      border-left: 5px solid var(--clr-cyan);
      height: 70%;
    }
  }
}

footer {
  background: var(--clr-very-dark-violet);
  color: white !important;
  //padding: 40px 0px;

  .logo {
    filter: brightness(0.8) invert(0.8);
  }

  h4 {
    color: var(--clr-gray);
  }

  ul {
    list-style: none;

    li {
      font-size: 16px;

      a {
        color: var(--clr-grayish-violet);
      }
    }
  }
  a {
    .v-icon {
      color: #fff;
    }
  }
  .copyright {
    background-color: #41415A;
    font-size: 15px;
  }
}

@media only screen and (min-width: 600px) {
  .jumbotron {
    margin: 0 1rem;

    .jumbotron-text {
      h1 {
        font-size: 45px;
      }
    }
  }
  .statistics {
    form {
      padding: 1.2rem 5rem !important;

      button {
        width: auto;
      }
    }

    .advance-statistic {
      margin: 0 auto;
    }

    .statistics-card {
      .card {
        .card-img {
          margin-left: 16px;
        }
      }
      .card-line-horizontal {
        display: none;
      }
    }
  }
  .boost-link {
    background: url("../assets/img/bg-boost-desktop.svg"), var(--clr-dark-violet);
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
    }
  }
  .statistics-card {
    .card-line {
      background-color: var(--clr-cyan);
      height: 4px;
      transform: translateY(8rem);
    }
  }
}
</style>
