<template>
  <div class="nav">
    <div class="navigation-desktop d-flex align-center"  :class="[ showMobileNav ? 'full' : 'half']">
      <div class="navigation-icon">
        <div v-if="showMobileNav" class="d-flex align-center">
          <img width="90rem" class="mt-1" src="../assets/img/logo.svg" />
        </div>
        <div v-if="!showMobileNav" class="d-flex align-center">
          <v-icon @click="showMobileNav = !showMobileNav">{{ icons.menu }}</v-icon>
          <img width="90rem" class="ml-3 mt-1" src="../assets/img/logo.svg" />
        </div>
      </div>
      <ul class="nav-menu nav-menu-left">
        <li class="ml-6">
          <router-link class="text-decoration-none" to="">Features</router-link>
        </li>
        <li class="ml-4">
          <router-link class="text-decoration-none" to="">Pricing</router-link>
        </li>
        <li class="ml-4">
          <router-link class="text-decoration-none" to="">Resources</router-link>
        </li>
      </ul>
      <ul class="nav-menu nav-menu-right ml-auto">
        <li>
          <router-link class="text-decoration-none" to="">Login</router-link>
        </li>
        <li class="ml-4">
          <router-link class="signup-btn text-decoration-none" to="">Sign Up</router-link>
        </li>
      </ul>
    </div>

    <transition name="sidebar">
      <div class="navigation-mobile" :class="[ showMobileNav ? 'show' : 'hide' ]">
        <div class="navigation-icon d-flex justify-end" @click="showMobileNav = !showMobileNav">
          <v-icon class="mr-3 close-btn">{{ icons.close }}</v-icon>
        </div>

        <ul>
          <li @click="showMobileNav = !showMobileNav">
            <router-link class="text-decoration-none" to="">Features</router-link>
          </li>
          <li @click="showMobileNav = !showMobileNav">
            <router-link class="text-decoration-none" to="">Pricing</router-link>
          </li>
          <li @click="showMobileNav = !showMobileNav">
            <router-link class="text-decoration-none" to="">Resources</router-link>
          </li>
          <v-divider class="ma-7" style="color: white"/>
          <li @click="showMobileNav = !showMobileNav">
            <router-link class="text-decoration-none btn" to="">Login</router-link>
          </li>
          <li class="signup-btn" @click="showMobileNav = !showMobileNav">
            <router-link class="text-decoration-none btn signup-btn" to="">Sign Up</router-link>
          </li>
        </ul>
        <div class="social-media text-center">
          <a class="text-decoration-none" href="#"><v-icon>{{ icons.twitter}}</v-icon></a>
          <a class="text-decoration-none mx-3" href="#"><v-icon>{{ icons.facebook }}</v-icon></a>
          <a class="text-decoration-none" href="#"><v-icon>{{  icons.instagram }}</v-icon></a>
        </div>
      </div>
    </transition>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import icons from '@/utils/icons'

export default Vue.extend({
  name: 'nav-bar' as string,
  data: () => ({
    icons,
    showMobileNav: false,
    closeMobileNav: true
  })
})
</script>

<style scoped lang="scss">
.close {
  display: none;
}
.nav {
  position: relative;
}
// desktop
.navigation-desktop {
  height: 55px;
  padding: 10px 6%;
  box-shadow: 0px 2px 2px rgba(0,0,0,0.23);
  .nav-menu {
    list-style: none;

    li a {
      color: var(--clr-grayish-violet);
      font-weight: 500;

      &:hover, &:active {
        color: var(--clr-very-dark-violet);
      }
    }
  }
  .nav-menu-right {
    li {
      font-size: 16px;

      a:hover {
        background:  var(--clr-cyan);
        color: #fff;
        padding: 5px 10px;
        border-radius: 50px;
      }
      .signup-btn {
        background: var(--clr-cyan);
        color: #fff;
        padding: 5px 10px;
        border-radius: 50px;
      }
    }

  }
}

@media only screen and (max-width: 767px) {
  .navigation-desktop {
    padding: 7px 3%;
  }
}

// mobile
.navigation-mobile {
  position: fixed;
  padding: 20px 0 0 0;
  width: 250px;
  transition: width 4s;
  background: var(--clr-dark-violet);
  margin-top: -55px;
  height: 100vh;
  z-index: 9999;
  text-align: center;

  .navigation-icon {
    .close-btn {
      position: absolute;
      top: 15px;
      padding: 4px;
      border-radius: 150px;
      background: linear-gradient(145deg, #cacaca, #f0f0f0);
      box-shadow:  22px 22px 100px #c7c7c7,
      -22px -22px 100px #f9f9f9;
      cursor: pointer;

      &:hover {
        transform: rotate(45deg);
      }
    }
  }
  ul {
    list-style: none;
    padding-left: 0px;

    li {
      margin-bottom: 15px;
      font-weight: 500;
      font-size: 18px;
      a {
        color: var(--clr-gray);

        &:hover {
          color: var(--clr-grayish-violet);
        }
      }

      .btn:hover {
        background: var(--clr-cyan);
        color: #fff;
        padding: 5px 30px;
        border-radius: 50px;
      }
    }
  }
  .social-media a .v-icon {
    filter: brightness(0) invert(1);
  }
}
.social-media {
  position: absolute;
  width: 100%;
  bottom: 20px;

  i {
    margin: 0 20px 0 0;
    color: #fff;
    font-size: 24rem;
  }

}
.full {
  transform: translateX(250px);
}
.nav-menu {
  display: none !important;
}
@media only screen and (min-width: 767.5px) {
  .navigation-icon div .v-icon {
    display: none;
  }
  .nav-menu {
    display: flex !important;
  }
}
.show {
  display: block;
}
.hide {
  display: none;
}
</style>
