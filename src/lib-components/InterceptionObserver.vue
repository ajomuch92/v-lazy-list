<template>
  <div ref="div" class="interception-observe-container" />
</template>

<script>

export default {
  name: 'InterceptionObserver',
  data: () => ({
    observe: null,
  }),
  mounted() {
    this.setObserve();
  },
  beforeDestroy() {
    if (this.observe) this.observe.unobserve(this.$refs.div);
  },
  methods: {
      setObserve() {
        const options = {
          threshold: 0,
        };
        this.observe = new IntersectionObserver(this.observeCallback, options);
        this.observe.observe(this.$refs.div);
      },
      observeCallback(entries) {
        const entry = entries[0];
        if (entry?.isIntersecting) {
          this.$emit('on-interception', entry);
        }
      },
  },
};
</script>

<style scoped>
    div {
        border: solid 1px transparent;
    }
</style>
