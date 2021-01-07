<template>
  <v-app :style="{background: $vuetify.theme.themes[theme].background}">
  <v-app-bar v-if="!isMobile"
      :collapse="!collapseOnScroll"
      :collapse-on-scroll="collapseOnScroll"
      app absolute
      color="transparent"
      dark flat
      scroll-target="#scrolling-techniques-6"
    >
      <div class="d-flex align-center pl-2">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="@/assets/logo.png"
          transition="scale-transition"
          width="40"
        />

        <v-toolbar-title v-model="collapseOnScroll"><h3>AU</h3></v-toolbar-title>
      </div>

      

      <v-spacer></v-spacer>

      <div class="d-flex justify-space-around">
        <v-btn
          href="https://dribbble.com/Kami_Dara/shots"
          target="_blank"
          text class="mr-10"
        >
          <span>Works</span>
        </v-btn>
        <v-btn
          href="https://github.com/vuetifyjs/vuetify/releases/latest"
          target="_blank"
          text class="mr-10"
        >
          <span>Resume</span>
        </v-btn>
        <v-btn
          href="mailto:adaugonnamene@gmail.com"
          target="_blank"
          text class="mr-10"
        >
          <span>Contact</span>
        </v-btn>
      </div>
    </v-app-bar>
    <v-toolbar v-else dark collapse max-width="72" color="#303030" max-height="80">
      <menu-icon @click="overlay = !overlay" size="1.5x" class="custom-class mx-auto"></menu-icon>
    </v-toolbar>

    <v-main>
      <HelloWorld/>
    </v-main>
    <v-overlay :opacity="opacity" :value="overlay">
       <x-icon @click="overlay = false" size="1.5x" class="custom-class" style="position: fixed; top: 5%; right: 1.5em; z-index: 99999;"></x-icon>
       <v-row class="text-center">
         <v-col cols="12">
        <v-btn
          href="https://dribbble.com/Kami_Dara/shots"
          target="_blank"
          text
        >
          <span>Works</span>
        </v-btn></v-col>
         <v-col cols="12">
        <v-btn
          href="https://github.com/vuetifyjs/vuetify/releases/latest"
          target="_blank"
          text
        >
          <span>Resume</span>
        </v-btn></v-col>
         <v-col cols="12">
        <v-btn
          href="mailto:adaugonnamene@gmail.com"
          target="_blank"
          text
        >
          <span>Contact</span>
        </v-btn></v-col>
       </v-row>
    </v-overlay>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import { MenuIcon } from 'vue-feather-icons'
import { XIcon } from 'vue-feather-icons'

export default {
  name: 'App',

  components: {
    HelloWorld,
    MenuIcon,
    XIcon
  },

  data: () => ({
    collapseOnScroll: true,
    isMobile: false,
    opacity: 0.9,
    overlay: false,
  }),

  computed:{
    theme(){
      return (this.$vuetify.theme.dark) ? 'dark' : 'light'
    }
  },
  mounted() {
    this.method1();
  },
  methods: {
    method1() {
      const isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent)
        if (isMobile) {
          this.isMobile = true;
        } else {
          this.isMobile = false;
        }
    },
  },
};
</script>

<style>
  h3 {
    color: #4B4B4B;
  }
</style>
