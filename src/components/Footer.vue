<template>
  <footer>
    Star Wars is a TM &amp; &copy; of LucasFilm Ltd. All data credited to <a href="https://swapi.dev/">swapi.dev</a>
  </footer>
</template>

<script lang="ts">
import {defineComponent} from 'vue';

export default defineComponent({
  name: 'Footer'
});
</script>

<style lang="sass">
  footer
    a
      color: #2c3e50
</style>