<script>
import Vue from 'vue';
import { VueLazyList } from '@/entry.esm';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    VueLazyList
  },
  data: () => ({
    items: [],
    loading: false,
  }),
  created() {
    this.loadRandomNumbers();
  },
  methods: {
    loadRandomNumbers() {
      this.loading = true;
      setTimeout(() => {
        for(let i = 0; i < 100; i+=1) {
          this.items.push(this.generateRandomNumber(1, 100))
        }
        this.loading = false;
      }, this.generateRandomNumber(800, 1000))
    },
    generateRandomNumber(begin, end) {
      return Math.floor(Math.random() * end) + begin;
    }
  }
});
</script>

<template>
  <div id="app">
    <vue-lazy-list :items="items" :loading="loading" @on-load-more="loadRandomNumbers">
      <template #item="{value}">
        <p>This is the item => {{value.item}} and this is the index => {{value.index}}</p>
      </template>
    </vue-lazy-list>
  </div>
</template>
