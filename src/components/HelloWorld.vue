<template>
  <v-container>

    <v-row :class="`text-center mt-${mRow}`">
      <v-col cols="12" :class="`mt-${mCol}`">
        <v-avatar class="avatar mt-4" :size="avatarSize">
          <img
            src="@/assets/aurora.png"
            alt="wendy" :contain="true"
          >
        </v-avatar>
      </v-col>

      <v-col cols="12" class="mb-4 white--text">
        <h1 :class="`display-${disp} text--primary font-weight-bold mb-3`" data-aos="zoom-in">
          Chinwendu Adaugo Nnamene
        </h1>

        <v-row justify="center">
          <v-col cols="12" lg="8" md="12" sm="12">
            <p class="text-center subheading font-weight-regular text--primary" data-aos="zoom-out">
              Hello ☺️ , I’m a freelance designer focused on UI/UX Design and Prototyping. I help companies define, design, and deliver the right product for the customer. I specialize in Product Design.
            </p>            
          </v-col>
        </v-row>
      </v-col>

      <v-col
        class="mb-5"
        cols="12"
      >
        <v-row justify="center" data-aos="fade-right">
          <a v-for="(link, i) in links" :key="i" :href="link.url"
            class="headline mx-3"
            target="_blank"
          >
            <span class="iconify" :style="`color: ${link.color};`" :data-icon="`simple-icons:${link.dataIcon}`" data-inline="false"></span>
          </a>
        </v-row>
      </v-col>

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
      <v-btn v-if="phone && birthDate == 18"
        color="secondary" bottom class="mb-3"
        fab text
       left fixed>
       <a href="https://1lib.eu/book/4098716/5451e0" target="_blank"><GiftBox/></a>
      </v-btn>
  </v-container>
</template>

<script>
import { SunIcon } from 'vue-feather-icons'
import { MoonIcon } from 'vue-feather-icons'
import GiftBox from '@/components/GiftBox.vue'

  export default {
    name: 'HelloWorld',
    props: ['phone', 'birthDate'],
    components: {
      SunIcon,
      MoonIcon,
      GiftBox,
    },
    data: () => ({
      avatarSize: 300,
      isDark: false,
      disp: 2,
      mRow: 10,
      mCol: 4,
      links: [
        {
          url: 'https://www.linkedin.com/in/wendy-nnamene-94478519a',
          dataIcon: 'linkedin',
          color: '#0A66C2'
        },
        {
          url: 'https://hashnode.com/@Wendy-Wu',
          dataIcon: 'hashnode',
          color: '#2962FF'
        },
        {
          url: 'https://dribbble.com/Kami_Dara/shots',
          dataIcon: 'dribbble',
          color: '#EA4C89'
        },
        {
          url: 'https://www.behance.net/adaugonnamene',
          dataIcon: 'behance',
          color: '#0057FF'
        },
      ]
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