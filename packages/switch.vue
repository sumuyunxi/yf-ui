<template>
  <div class="yf-switch" @click="handleClick"
  :class="{
    'is-checked':value
  }">
    <span class="yf-switch_core" ref="core">
      <span class="yf-switch_button"></span>
    </span>
    <input type="checkbox" class="yf-switch_input" :name="name" ref="input">
  </div>
</template>

<script>
export default {
  name: 'YfSwitch',
  props: {
    value: {
      type: Boolean,
      default: false
    },
    activeColor: {
      type: String,
      default: ''
    },
    inactiveColor: {
      type: String,
      default: ''
    },
    name: {
      type: String,
      default: ''
    }
  },
  mounted () {
    this.setColor()
    this.$refs.input.checked = this.value
  },
  methods: {
    handleClick () {
      this.$emit('input', !this.value)
      this.$nextTick(function () {
        this.setColor()
        this.$refs.input.checked = this.value
      })
    },
    setColor () {
      if (this.activeColor || this.inactiveColor) {
        const color = this.value ? this.activeColor : this.inactiveColor
        this.$refs.core.style.borderColor = color
        this.$refs.core.style.backgroundColor = color
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  .yf-switch{
    display: inline-block;
    align-items: center;
    position: relative;
    font-size: 14px;
    line-height: 20px;
    vertical-align: middle;
    .yf-switch_core{
    margin: 0;
    display: inline-block;
    position: relative;
    width: 40px;
    height: 20px;
    border: 1px solid #dcdfe6;
    outline: none;
    border-radius: 10px;
    box-sizing: border-box;
    background: #dcdfe6;
    cursor: pointer;
    transition: border-color .3s,background-color .3s;
    vertical-align: middle;
    .yf-switch_button{
      position:absolute;
      top: 1px;
      left: 1px;
      border-radius: 100%;
      transition: all .3s;
      width: 16px;
      height: 16px;
      background-color: #fff;
      }
    }
  }
    // 选中样式
  .is-checked {
    .yf-switch_core{
      border-color: #409eff;
      background-color: #409eff;
      .yf-switch_button {
        transform: translateX(20px);
      }
    }
  }
    //隐藏input标签
  .yf-switch_input{
    position:absolute;
    width: 0;
    height: 0;
    opacity: 0;
    margin: 0;
  }
</style>
