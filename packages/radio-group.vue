<template>
  <div class="yf-radio-group">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'YfRadioGroup',
  props: {
    value: null
  },
  provide () {
    return {
      radioGroup: this
    }
  }
}
</script>

<style>

</style>
