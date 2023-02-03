<template>
  <div class="yf-checkbox-group">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'YfCheckboxGroup',
  props: {
    value: {
      type: Array
    }
  },
  provide () {
    return {
      checkboxGroup: this
    }
  }
}
</script>

<style>

</style>
