<template>
  <div class="side-slider" :style="slidePosition">
    <slot></slot>
    <el-button @click.self="close">关闭</el-button>
  </div>
</template>
<script>
  export default {
    props: {
      visible: {
        type: Boolean,
        default: false
      },
      width: {
        type: Number,
        default: 200
      },
      direction: String
    },
    data () {
      return {
        slidePosition: {
          right: '-200px',
          top: 0,
          width: this.width
        }
      }
    },
    watch: {
      visible (val) {
        if (val) {
          this.slidePosition.right = 0
        } else {
          this.slidePosition.right = '-' + this.width + 'px'
        }
      }
    },
    methods: {
      close () {
        this.$emit('update:visible', false)
      }
    }
  }
</script>
<style>
  .side-slider {
    position: fixed;
    background: #eee;
    height: 100%;
    transition: right 1s;
    z-index: 10;
  }
</style>
