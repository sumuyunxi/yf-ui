<template>
  <form class="yf-form">
    <slot></slot>
  </form>
</template>

<script>
export default {
  name: 'YfForm',
  props: {
    model: {
      type: Object,
      required: true
    },
    labelWidth: {
      type: String,
      default: '80px'
    }
  },
  provide () {
    return {
      form: this
    }
  }
}
</script>

<style>

</style>
