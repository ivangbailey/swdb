<template>
  <Nav v-bind:navItems="navItems" @navToggle="navToggle"/>
  <Search v-bind:endpoint="navItems[activeNavIndex].label" @fetchResults="fetchResults"/>
  <SearchResults v-bind:results="results" />
  <Footer />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import axios, { AxiosResponse } from 'axios';
import Nav from './components/Nav.vue';
import Footer from './components/Footer.vue';
import Search from './components/Search.vue';
import SearchResults from './components/SearchResults.vue';

export default defineComponent({
  name: 'App',
  data() {
    return {
      activeNavIndex: 0,
      navItems: [
        {
          id: 0,
          label: 'planets',
          active: true
        },
        {
          id: 1,
          label: 'people',
          active: false
        },
        {
          id: 2,
          label: 'starships',
          active: false
        }
      ],
      results: []
    }
  },
  methods: {
    navToggle(id: number) {
      this.navItems[this.activeNavIndex].active = false;
      this.activeNavIndex = id;
      this.navItems[id].active = true;
    },

    fetchResults(url: string) {
      axios.get(url)
        .then((response: AxiosResponse<any>) => {
          this.results = response.data.results;
          console.log(response);
        })
    }
  },
  components: {
    Nav,
    Search,
    SearchResults,
    Footer
  },
  // emits: [
  //   'navToggle'
  // ]
});
</script>

<style lang="sass">
  body, html
    background-color: black
    margin: 0
    padding: 0

  h1, h2, h3, a
    color: #ffe81f

  #app
    font-family: Avenir, Helvetica, Arial, sans-serif
    -webkit-font-smoothing: antialiased
    -moz-osx-font-smoothing: grayscale
    color: #2c3e50
    margin: 1em auto
    max-width: 80%

</style>
