<template>
<transition>
    <!-- 对话框的遮罩 -->
 <div class="yf-dialog_wrapper" v-show="visible" @click.self="handleClick">
    <!-- dialog主体 -->
   <div class="yf-dialog" :style="{width,marginTop:top}" >
     <div class="yf-dialog_header">
        <slot name="title">
            <span class="yf-dialog_title">{{title}}</span>
        </slot>

       <button class="yf-dialog_headerbtn" @click="handleClick">
         <i class="one-icon-close"></i>
       </button>
     </div>
     <div class="yf-dialog_body">
       <span>
        <!-- 使用默认插槽传递内容 -->
        <slot></slot>
        </span>
     </div>
     <div class="yf-dialog_footer" v-if="$slots.footer">
       <slot name="footer"></slot>
     </div>
   </div>
 </div>
 </transition>

</template>

<script>
export default {
  name: 'YfDialog',
  props: {
    title: {
      type: String,
      default: '提示'
    },
    width: {
      type: String,
      default: '50%'
    },
    top: {
      type: String,
      default: '20vh'
    },
    visible: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    handleClick () {
      this.$emit('update:visible', false)
    }
  }
}
</script>

<style lang="scss" scoped>
.v-enter-active{
    animation: run .5s;
}
.v-leave-active{
    animation: run .5s reverse;
}
@keyframes run {
    0%{
        opacity: 0;
        transform: translateY(-20px);
    }
    100%{
        opacity: 1;
        transform: translateY(0px);
    }
}
.yf-dialog_wrapper{
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  overflow: auto;
  margin: 0;
  z-index: 2001;
  background-color: rgba(0,0,0,0.5);
  .yf-dialog{
    position: relative;
    margin: 15vh auto 50px;
    background: #fff;
    border-radius: 2px;
    box-shadow: 0 1px 3px rgba(0,0,0,0.3);
    box-sizing: border-box;
    width: 30%;
    &_header{
      padding: 20px 20px 10px;
      .yf-dialog_title{
        line-height: 24px;
        font-size: 18px;
        color: #303133;
      }
      .yf-dialog_headerbtn{
        position: absolute;
        top: 20px;
        right: 20px;
        padding: 0;
        background: transparent;
        border: none;
        outline: none;
        cursor: pointer;
        font-size: 16px;
        .one-icon-close{
          color:909399
        }
      }
    }
    &_body{
      padding: 30px 20px;
      color: #606266;
      font-size: 14px;
      word-break: break-all;
    }
    &_footer{
      padding: 10px 20px 20px;
      text-align: right;
      box-sizing: border-box;
      ::v-deep .yf-button:first-child{
        margin-right: 20px;
      }
    }
  }
}
</style>
