<template>
  <n-icon :size="size" :color="color" :depth="depth" :component="component" />
</template>

<script setup>
import {h, defineProps, computed} from 'vue'
import {NIcon} from 'naive-ui'

const props = defineProps({
  type: {
    type: String,
    required: true
  },
  size: {
    type: [String, Number],
    default: undefined
  },
  color: {
    type: String,
    default: undefined
  },
  depth: {
    type: [String, Number],
    default: undefined
  }
})

// 创建SVG图标组件
const component = computed(() => {
  return {
    render() {
      return h('svg', {
        'aria-hidden': true,
        class: 'icon-font',
      }, [
        h('use', {
          'xlink:href': `#${props.type}`
        })
      ])
    }
  }
})
</script>

<style scoped>
.icon-font {
  width: 1em;
  height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}
</style>