<template>
  <TransitionGroup tag="ul" name="list" class="list" @before-leave="onBeforeLeave" data-empty="Ingen opgaver">
    <slot />
    <ListItem v-for="(item, index) in modelValue" :key="item" :model-value="item" @remove="onRemove" :focus="focus == index" />
  </TransitionGroup>
</template>

<script>
import ListItem from './ListItem.vue'
export default {
  name: 'List',
  components: { ListItem },
  props: {
    modelValue: {
      type: Array,
      default: []
    },
    focus: {
      default: 0
    }
  },
  methods: {
    onRemove(item) {
      this.$emit('remove', item)
    },
    onBeforeLeave(el) {
      const items = [...el.parentElement.children]
      const index = items.indexOf(el)
      const height = el.offsetHeight
      const halfHeight = height / 2
      let top = el.offsetTop
      if (index == items.length - 1) {
        if (items.length == 1) {
          top = halfHeight
        } else {
          top -= height
        }
      }
      el.style.top = `${top - halfHeight}px`
    }
  }
}
</script>
