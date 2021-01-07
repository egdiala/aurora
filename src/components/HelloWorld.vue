<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12" class="mt-4">
        <v-avatar class="avatar" :size="avatarSize">
          <img
            src="@/assets/aurora.png"
            alt="aurora" :contain="true"
          >
        </v-avatar>
      </v-col>

      <v-col class="mb-4 white--text">
        <h1 :class="`display-${disp} font-weight-bold mb-3`">
          Chinwendu Adaugo Nnamene
        </h1>

        <p class="text-center subheading font-weight-regular">
          Hi 👋 , I’m a Product Designer in Port Harcourt, Nigeria. I specialize in UI/UX Design.
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
      <v-btn
        color="secondary" bottom class="mb-3"
        fab dark
       right fixed>
        <sun-icon size="1.5x" class="custom-class"></sun-icon>
      </v-btn>
  </v-container>
</template>

<script>
import { SunIcon } from 'vue-feather-icons'

  export default {
    name: 'HelloWorld',
  components: {
    SunIcon
  },
    data: () => ({
      ecosystem: [
        {
          text: 'vuetify-loader',
          href: 'https://github.com/vuetifyjs/vuetify-loader',
        },
        {
          text: 'github',
          href: 'https://github.com/vuetifyjs/vuetify',
        },
        {
          text: 'awesome-vuetify',
          href: 'https://github.com/vuetifyjs/awesome-vuetify',
        },
      ],
      importantLinks: [
        {
          text: 'Documentation',
          href: 'https://vuetifyjs.com',
        },
        {
          text: 'Chat',
          href: 'https://community.vuetifyjs.com',
        },
        {
          text: 'Made with Vuetify',
          href: 'https://madewithvuejs.com/vuetify',
        },
        {
          text: 'Twitter',
          href: 'https://twitter.com/vuetifyjs',
        },
        {
          text: 'Articles',
          href: 'https://medium.com/vuetify',
        },
      ],
      whatsNext: [
        {
          text: 'Explore components',
          href: 'https://vuetifyjs.com/components/api-explorer',
        },
        {
          text: 'Select a layout',
          href: 'https://vuetifyjs.com/getting-started/pre-made-layouts',
        },
        {
          text: 'Frequently Asked Questions',
          href: 'https://vuetifyjs.com/getting-started/frequently-asked-questions',
        },
      ],
      avatarSize: 300,
      disp: 2
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
          } else {
            this.avatarSize = 300;
            this.disp = 2;
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
</style>