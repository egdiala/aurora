<template>
  <v-container>

    <v-row :class="`text-center mt-${mRow}`">
      <v-col cols="12" :class="`mt-${mCol}`">
        <v-avatar class="avatar mt-4" :size="avatarSize">
          <img
            src="@/assets/aurora.png"
            alt="aurora" :contain="true"
          >
        </v-avatar>
      </v-col>

      <v-col class="mb-4 white--text">
        <h1 :class="`display-${disp} text--primary font-weight-bold mb-3`">
          Chinwendu Adaugo Nnamene
        </h1>

        <p class="text-center subheading font-weight-regular text--primary">
          Hi 👋 , I’m a UI/UX Designer in Port Harcourt, Nigeria. I specialize in Product Design.
        </p>
      </v-col>

      <!-- <v-col
        class="mb-5"
        cols="12"
      >
        <h2 class="headline font-weight-bold mb-3">
          What's next?
        </h2>

        <v-row justify="center">
          <a
            v-for="(next, i) in whatsNext"
            :key="i"
            :href="next.href"
            class="subheading mx-3"
            target="_blank"
          >
            {{ next.text }}
          </a>
        </v-row>
      </v-col>

      <v-col
        class="mb-5"
        cols="12"
      >
        <h2 class="headline font-weight-bold mb-3">
          Important Links
        </h2>

        <v-row justify="center">
          <a
            v-for="(link, i) in importantLinks"
            :key="i"
            :href="link.href"
            class="subheading mx-3"
            target="_blank"
          >
            {{ link.text }}
          </a>
        </v-row>
      </v-col>

      <v-col
        class="mb-5"
        cols="12"
      >
        <h2 class="headline font-weight-bold mb-3">
          Ecosystem
        </h2>

        <v-row justify="center">
          <a
            v-for="(eco, i) in ecosystem"
            :key="i"
            :href="eco.href"
            class="subheading mx-3"
            target="_blank"
          >
            {{ eco.text }}
          </a>
        </v-row>
      </v-col> -->
    </v-row>
      <v-btn @click="$vuetify.theme.dark = !$vuetify.theme.dark"
        color="secondary" bottom class="mb-3"
        fab dark
       right fixed>
       <transition name="slide-fade">
        <sun-icon v-if="$vuetify.theme.dark == false" size="1.5x" class="custom-class"></sun-icon>
       </transition>
       <transition name="slide-fade">
        <moon-icon v-if="$vuetify.theme.dark == true" size="1.5x" class="custom-class"></moon-icon>
       </transition>
      </v-btn>
  </v-container>
</template>

<script>
import { SunIcon } from 'vue-feather-icons'
import { MoonIcon } from 'vue-feather-icons'

  export default {
    name: 'HelloWorld',
  components: {
    SunIcon,
    MoonIcon
  },
    data: () => ({
      avatarSize: 300,
      isDark: false,
      disp: 2,
      mRow: 10,
      mCol: 4
    }),
    mounted() {
      this.method1();
    },
    methods: {
      method1() {
        const isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent)
          if (isMobile) {
            this.avatarSize = 200;
            this.disp = 1;
            this.mRow = 5;
            this.mCol = 2;
          } else {
            this.avatarSize = 300;
            this.disp = 2;
            this.mRow = 10;
            this.mCol = 4;
          }
      },
    },
  }
</script>

<style scoped>
@keyframes float {
	0% {
		box-shadow: 0 5px 15px 0px rgba(0,0,0,0.6);
		transform: translatey(0px);
	}
	50% {
		box-shadow: 0 25px 15px 0px rgba(0,0,0,0.2);
		transform: translatey(-20px);
	}
	100% {
		box-shadow: 0 5px 15px 0px rgba(0,0,0,0.6);
		transform: translatey(0px);
	}
}

.avatar {
	transform: translatey(0px);
	animation: float 6s ease-in-out infinite;
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