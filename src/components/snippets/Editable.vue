<template>
  <div class="editable" ref="editable" contenteditable @input="onInput" @keydown.enter="onKeydown" @blur="blur" tabindex="0" />
</template>

<script>
import { ref } from 'vue'
export default {
  name: 'Editable',
  props: {
    modelValue: {
      type: String,
      default: ''
    },
    text: {
      default: ''
    },
    newline: {
      default: false
    },
    focus: {
      default: false
    },
    blur: {
      default: null
    }
  },
  setup() {
    const editable = ref('')
    return { editable }
  },
  mounted() {
    this.$refs.editable.innerText = this.modelValue
    if (this.focus) {
      this.$refs.editable.focus()
    }
  },
  methods: {
    onInput(e) {
      this.$emit('update:modelValue', e.target.innerText)
    },
    onKeydown(e) {
      if (!this.newline) {
        e.preventDefault();
        e.target.blur();
      }
    }
  }
}
</script>
