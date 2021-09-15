<template>
  <div class="search-results" v-if="results.length > 0">
    <ul>
      <li v-for="(key, index) of results" :key="index" v-bind:class="{active: index === activeResult}">
        <template v-if="index === activeResult" @click="setActiveResult(-1)">
          <SearchResult v-bind:result="results[index]" />
        </template>
        <span v-else @click="setActiveResult(index)">
          {{results[index].name}}
        </span>
      </li>
    </ul>
  </div>
  <div v-else class="search-results">
    {{propsNotFound()}}
  </div>
</template>

<script lang="ts">
import {defineComponent} from 'vue';
import SearchResult from './SearchResult.vue';

export default defineComponent({
  name: 'Search',
  data() {
    return {
      activeResult: -1
    }
  },
  methods: {
    setActiveResult(index: number) {
      this.activeResult = index;
      console.log(index);
    },
    propsNotFound() {
      return 'no results for ${query}';
    }
  },
  props: {
    results: Array
  },
  components: {
    SearchResult
  }
});

</script>

<style lang="sass" scoped>
  .search-results
    min-height: 300px
  li
    list-style: disclosure-closed
  .active
    list-style: disclosure-open
  ul
    color: #2C3E34
</style>
