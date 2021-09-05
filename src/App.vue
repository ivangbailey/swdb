<template>
  <Nav v-bind:navItems="navItems"/>
  <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" /> -->
</template>

<script lang="ts">
import { defineComponent } from 'vue';
// import HelloWorld from './components/HelloWorld.vue';
import Nav from './components/Nav.vue';


export default defineComponent({
  name: 'App',
  data() {
    return {
      activeNavItem: 0,
      navItems: [
        {
          id: 0,
          label: 'planets',
          active: true
        },
        {
          id: 1,
          label: 'characters',
          active: false
        },
        {
          id: 2,
          label: 'vehicles',
          active: false
        }
      ]
    }
  },
  methods: {
    navToggle(id: number) {
      this.navItems[this.activeNavItem].active = false;
      this.activeNavItem = id;
      this.navItems[id].active = true;
    }
  },
  components: {
    // HelloWorld,
    Nav
  },
  emits: ['navToggle']
});
</script>

<style lang="sass">
body, html
  background-color: black

h1, h2, h3
  color: #ffe81f

#app
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  color: #2c3e50
  margin-top: 60px


</style>
