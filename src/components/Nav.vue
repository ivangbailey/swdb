<template>
<nav>
  <div id="logo-container">
    <img alt="Star Wars logo" src="https://upload.wikimedia.org/wikipedia/commons/6/6c/Star_Wars_Logo.svg">
  </div>
  <div>
    <ul id="navigation-list">
      <li v-for="item in navItems" :key="item.id">
        <div v-if="item.active" class="active">
          <strong >{{item.label}}</strong>
        </div>
        <div v-else @click="$emit('navToggle', item.id)">
            {{item.label}}

        </div>
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
  methods: {
    // onClick(): void {

    // }
  },
  props: {
    navItems: Array
  }
});
</script>

<style lang="sass" scoped>
  nav
    width: 100%
  ul
    list-style-type: none
    li
      margin: 0 .5em
      display: inline-block

  #logo-container
    max-width: 8em
    margin: 1em auto

  img
    max-width: 100%
</style>