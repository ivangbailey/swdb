<template>
  <div class="active">
    <ul>
      <span v-for="(value, key) in result" :key="key">
        <li>
          <strong>{{key}}</strong>
          {{value}}
        </li>
      </span>
    </ul>
  </div>
</template>

<script lang="ts">
import {defineComponent} from 'vue';

export default defineComponent({
  name: 'SearchResult',
  props: {
    result: Object
  }
});
</script>

<style lang="sass" scoped>
  dt
    margin-bottom: 0

</style>