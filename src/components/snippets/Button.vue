<template>
  <button ref="button" @click.prevent="onClick">
    <slot />
  </button>
</template>

<script>
import { ref } from 'vue'
export default {
  name: 'Button',
  props: {
    modelValue: {
      type: Boolean,
      default: false
    }
  },
  setup() {
    const button = ref('')
    return { button }
  },
  methods: {
    onClick() {
      this.$emit('update:modelValue')
    }
  }
}
</script>
