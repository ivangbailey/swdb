<template>
  <input type="text" placeholder="keywords here" v-model="query" />
  <button @click="search">search</button>
  <div class="error">{{searchStatus}}</div>
</template>

<script lang="ts">
import {defineComponent} from 'vue';

const SWAPI = 'https://swapi.dev/api/';

export default defineComponent({
  name: 'Search',
  data() {
    return {
      query: '',
      searchStatus: ''
    }
  },
  methods: {
    search() {
      if (this.query === '') {
        this.searchStatus = 'search query cannot be empty';
        return;
      }
      const API_URL = SWAPI + this.endpoint + '/?search=' + this.query;
      this.searchStatus = '';
      this.$emit('fetchResults', API_URL);
    },
  },
  props: {
    endpoint: String
  }

});

</script>


<style lang="sass">
  .error
    color: red
</style>