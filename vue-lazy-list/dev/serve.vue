<script>
import Vue from 'vue';
// Uncomment import and local "components" registration if library is not registered globally.
// import { VueLazyListSample } from '@/entry.esm';

export default Vue.extend({
  name: 'ServeDev',
  // components: {
  //  VueLazyListSample,
  // }
});
</script>

<template>
  <div id="app">
    <vue-lazy-list-sample />
  </div>
</template>
