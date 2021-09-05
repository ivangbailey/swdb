<template>
<nav>
  <div id="logo-container">
    <img alt="Star Wars logo" src="https://upload.wikimedia.org/wikipedia/commons/6/6c/Star_Wars_Logo.svg">
  </div>
  <div>
    <ul id="navigation-list">
      <li v-for="item in navItems" :key="item.id">
        <strong v-if="item.active">{{item.label}}</strong>
        <div @click="navToggle(item.id)" v-else>{{item.label}}</div>
      </li>
    </ul>
    <!-- {{navItems}} -->
  </div>
</nav>
</template>


<script lang="ts">
import {defineComponent} from 'vue';

export default defineComponent({
  name: 'Nav',
  data() {
    return {
      active: 0
    }
  },
  methods: {
    onClick(): void {
      console.log('clicked nav item');
    }
  },
  props: {
    navItems: Array
  }
});
</script>

<style lang="sass">
#logo-container
  max-width: 8em
  margin: 1em auto

img
  max-width: 100%
</style>