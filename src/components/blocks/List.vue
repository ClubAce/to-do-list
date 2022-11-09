<template>
  <div class="list">
    <slot />
    <ListItem v-for="item in modelValue" :key="item" :model-value="item" />
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
    }
  }
}
</script>
