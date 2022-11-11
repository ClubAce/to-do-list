<template>
  <div class="list" data-empty="Ingen opgaver">
    <slot />
    <ListItem v-for="(item, index) in modelValue" :key="item" :model-value="item" @remove="onRemove" :focus="focus == index" />
  </div>
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
    }
  }
}
</script>
