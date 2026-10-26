<script>
import Navbar from './components/Navbar.vue';
import HomeView from './components/HomeView.vue';
import AboutView from './components/AboutView.vue';
import ContactView from './components/ContactView.vue';
import Footer from './components/Footer.vue';
import Services from './components/Services.vue';


export default {
  components: {
    Navbar, HomeView, AboutView, ContactView, Footer, Services
  },
  data() {
    return {
      page: 'home',

    }
  },
  methods: {
    showHome(i) {
      this.page = i;
    },

  }

}

</script>


<template>
  <Navbar @go-home="showHome" />
  <HomeView v-if="page === 'home'" />
  <AboutView v-if="page === 'about'" />
  <Services v-if="page === 'services'"/>
  <ContactView v-if="page === 'contact'" />
  <Footer />
</template>
