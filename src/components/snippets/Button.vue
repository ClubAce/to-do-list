<template>
  <button>
    <slot />
  </button>
</template>

<script>
import { ref } from 'vue'
export default {
  name: 'Button',
  props: {
    click: {
      default: false
    }
  },
  setup() {
    const button = ref('')
    return { button }
  },
  mounted() {
    this.$refs.button.checked = this.checked
  },
  methods: {
    onChange(e) {
      this.$emit('update:modelValue', e.target.checked)
    }
  }
}
</script>
