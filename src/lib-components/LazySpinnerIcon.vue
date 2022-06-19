<template>
  <span class="spinner" />
</template>

<script>
export default {
  name: 'LazySpinnerIcon',
}
</script>

<style scoped>
  .spinner {
    width: 25px;
    height: 25px;
    border-radius: 50%;
    border-width: 3px;
    border-style: solid;
    border-color: #353535 transparent transparent transparent;
    animation: spinner1 1s linear infinite;
  }

  @keyframes spinner1 {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
</style>