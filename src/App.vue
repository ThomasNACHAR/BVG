<script>

import Header from "@/components/Header.vue"
import Home from "@/components/Home.vue"
import Footer from "@/components/Footer.vue"
import Circuit from "@/components/Circuit.vue"
import Partenaires from "@/components/Partenaires.vue"
import Reservation from "@/components/Reservation.vue"
import Contact from "@/components/Contact.vue"

export default {
  components: {
    Header,
    Home,
    Footer,
    Circuit,
    Partenaires,
    Reservation,
    Contact
  },
  data() {
    return {
      isMobile: this.checkIfMobile(),
      pageToggled: "home"
    }
  },
  mounted() {
    window.addEventListener('resize', this.handleResize);
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.handleResize);
  },
  methods: {
    togglePage(page) {
      this.pageToggled = page
    },
    checkIfMobile() {
      return window.innerWidth <= 1024
    },
    scrollTop() {
      document.documentElement.scrollTop = 0
    },
    isTop() {
      return window.scrollY === 0
    }
  }
}

</script>

<template>
  
  <Header @toggle-page="togglePage" v-if="!isMobile"></Header>
  <button v-if="!isTop" @click="scrollTop">appuyez !</button>
  <Home v-if="pageToggled=='home'&&!isMobile"></Home>
  <Circuit v-if="pageToggled=='circuit'"></Circuit>
  <Partenaires v-if="pageToggled=='partenaires'"></Partenaires>
  <Reservation v-if="pageToggled=='reservation'"></Reservation>
  <Contact v-if="pageToggled=='contact'"></Contact>
  <Footer v-if="!isMobile"></Footer>
  
</template>

<style>
</style>
