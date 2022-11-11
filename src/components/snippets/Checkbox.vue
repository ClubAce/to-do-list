<template>
  <label class="checkbox">
    <input type="checkbox" :checked="modelValue" @input="onInput">
    <span class="checkmark" />
  </label>
</template>

<script>
export default {
  name: 'Checkbox',
  props: {
    modelValue: {
      type: Boolean,
      default: false
    },
  },
  methods: {
    onInput(e) {
      this.$emit('update:modelValue', e.target.checked)
    }
  }
}
</script>
