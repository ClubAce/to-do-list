<template>
  <label class="checkbox">
    <input type="checkbox" ref="checkbox" @change="onChange">
    <span class="checkmark" />
  </label>
</template>

<script>
import { ref } from 'vue'
export default {
  name: 'Checkbox',
  props: {
    checked: {
      default: false
    }
  },
  setup() {
    const checkbox = ref('')
    return { checkbox }
  },
  mounted() {
    this.$refs.checkbox.checked = this.checked
  },
  methods: {
    onChange(e) {
      this.$emit('update:modelValue', e.target.checked)
    }
  }
}
</script>
