<template>
  <div class="list-item">
    <div class="list-item__checkbox">
      <Checkbox v-model="modelValue.checked" :checked="modelValue.checked" @change="onUpdate" ref="checkbox" />
    </div>
    <Editable class="list-item__task" v-model="modelValue.text" @blur="onUpdate(), onBlur()" :focus="focus" ref="editable" />
    <div class="list-item__remove" />
  </div>
</template>

<script>
import { ref } from 'vue'
import Checkbox from '../snippets/Checkbox.vue'
import Editable from '../snippets/Editable.vue'
export default {
  name: 'ListItem',
  components: { Checkbox, Editable },
  props: {
    modelValue: {
      type: Object,
      default: {}
    },
    item: {
      default: {}
    },
    focus: {
      default: false
    },
    blur: {
      default: null
    }
  },
  setup() {
    const checkbox = ref('')
    const editable = ref('')
    return { checkbox, editable }
  },
  methods: {
    onUpdate() {
      this.$emit('update:modelValue', this.modelValue)
    },
    onBlur() {
      this.$emit('blur')
    }
  }
}
</script>
