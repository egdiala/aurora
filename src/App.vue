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
          text class="mr-10 text--primary text-body-1"
        >
          <span>Works</span>
        </v-btn>
        <v-btn
          target="_blank"
          text class="mr-10 text--primary text-body-1"
        >
          <span>Resume</span>
        </v-btn>
        <v-btn
          href="mailto:adaugonnamene@gmail.com"
          target="_blank"
          text class="mr-10 text--primary text-body-1"
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
       <transition name="slide-fade">
      <div id="balloon-container" style="position: fixed; z-index: 0;" v-show="showBalloons"></div>
       </transition>
    <v-overlay :opacity="opacity" :value="overlay">
       <x-icon @click="overlay = false" size="1.5x" class="custom-class" style="position: fixed; top: 5%; right: 1.5em; z-index: 99999;"></x-icon>
       <v-row class="text-center">
         <v-col cols="12">
        <v-btn
          href="https://dribbble.com/Kami_Dara/shots"
          target="_blank" class="text--primary"
          text
        >
          <span>Works</span>
        </v-btn></v-col>
         <v-col cols="12">
        <v-btn
          target="_blank" class="text--primary"
          text
        >
          <span>Resume</span>
        </v-btn></v-col>
         <v-col cols="12">
        <v-btn
          href="mailto:adaugonnamene@gmail.com"
          target="_blank" class="text--primary"
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
    opacity: 0.9,
    overlay: false,
    showBalloons: true
  }),

  computed:{
    theme(){
      return (this.$vuetify.theme.dark) ? 'dark' : 'light'
    },
    isMobile(){
      const isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);
      return isMobile;
    }
  },
  mounted() {
    this.$vuetify.theme.dark = true;
    this.createBalloons(10);
    setTimeout(() => {
      this.showBalloons = false;
    }, 15000);
  },
  methods: {
      random(num) {
        return Math.floor(Math.random()*num)
      },
      getRandomStyles() {
        var r = this.random(255);
        var g = this.random(255);
        var b = this.random(255);
        var mt = this.random(200);
        var ml = this.random(50);
        var dur = this.random(5)+5;
        return `
        background-color: rgba(${r},${g},${b},0.7);
        color: rgba(${r},${g},${b},0.7); 
        box-shadow: inset -7px -3px 10px rgba(${r-10},${g-10},${b-10},0.7);
        margin: ${mt}px 0 0 ${ml}px;
        animation: float ${dur}s ease-in infinite
        `
      },
      createBalloons(num) {
        var balloonContainer = document.getElementById("balloon-container");
        for (var i = num; i > 0; i--) {
        var balloon = document.createElement("div");
        balloon.className = "balloon";
          balloon.style.cssText = this.getRandomStyles();
        if (this.showBalloons == true) {
          console.log(this.showBalloons);
        balloonContainer.append(balloon);
        }
        }
      },

  }
};
</script>

<style>
  h3 {
    color: #4B4B4B;
  }
  #balloon-container {
  height: 100vh;
  padding: 1em;
  box-sizing: border-box;
  display: flex;
  flex-wrap: wrap;
  overflow: hidden;
}

.balloon {
  height: 125px;
  width: 105px;
  border-radius: 75% 75% 70% 70%;
  position: relative;
}

.balloon:before {
  content: "";
  height: 75px;
  width: 1px;
  padding: 1px;
  background-color: #FDFD96;
  display: block;
  position: absolute;
  top: 125px;
  left: 0;
  right: 0;
  margin: auto;
}

.balloon:after {
    content: "▲";
    text-align: center;
    display: block;
    position: absolute;
    color: inherit;
    top: 120px;
    left: 0;
    right: 0;
    margin: auto;
}

@keyframes float {
  from {transform: translateY(100vh);
  opacity: 1;}
  to {transform: translateY(-300vh);
  opacity: 0;}
}

.slide-fade-enter-active {
  transition: all 0.3s ease;
}
.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
</style>