<template>
  <div class="input" ref="input" @input="onInput" @keydown.enter="onEnter" contenteditable tabindex="0" />
</template>

<script>
import { ref } from 'vue'
export default {
  name: 'Input',
  props: {
    modelValue: {
      type: String,
      default: ''
    },
    newline: {
      default: false
    },
    focus: {
      default: false
    }
  },
  setup() {
    const input = ref('')
    return { input }
  },
  mounted() {
    this.$refs.input.innerText = this.modelValue
    if (this.focus) {
      this.$refs.input.focus()
    }
  },
  methods: {
    onInput(e) {
      this.$emit('update:modelValue', e.target.innerText)
    },
    onEnter(e) {
      if (!this.newline) {
        e.preventDefault()
        e.target.blur()
      }
    }
  }
}
</script>
