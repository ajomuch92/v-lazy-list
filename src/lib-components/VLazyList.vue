<template>
  <ul class="v-lazy-list">
    <li v-for="(item, key) in items" :key="key">
      <slot name="item" v-bind:value="{item, index: key}"/>
    </li>
    <interception-observer @on-interception="interceptionHandler" />
    <div v-if="loading" class="icon-container">
      <slot name="icon">
        <lazy-spinner-icon />
      </slot>
    </div>
  </ul>
</template>

<script>
import InterceptionObserver from './InterceptionObserver.vue';
import LazySpinnerIcon from './LazySpinnerIcon.vue';

export default {
  name: 'VueLazyList',
  components: { LazySpinnerIcon, InterceptionObserver },
  props: {
    items: {
      type: Array,
      required: true,
    },
    loading: {
      type: Boolean,
      default: false,
    }
  },
  data: () => ({
    isLoadingMore: false,
  }),
  watch: {
    items() {
      this.isLoadingMore = false;
    },
  },
  methods: {
    interceptionHandler() {
      if (!this.isLoadingMore) {
        this.isLoadingMore = true;
        this.$emit('on-load-more');
      }
    },
  }
}
</script>

<style scoped>
  ul.v-lazy-list {
    padding-left: 0px;
  }

  .v-lazy-list li {
    list-style-type: none;
  }

  .icon-container {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>