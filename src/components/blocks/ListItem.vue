<template>
  <li class="list-item">
    <div class="list-item__checkbox">
      <Checkbox v-model="modelValue.done" />
    </div>
    <Input class="list-item__task" v-model="modelValue.task" :focus="focus" placeholder="Opgavebeskrivelse" />
    <div class="list-item__remove">
      <div class="icon icon-button trash" @click="onClick" title="Slet opgave" />
    </div>
  </li>
</template>

<script>
import Checkbox from '../snippets/Checkbox.vue'
import Input from '../snippets/Input.vue'
export default {
  name: 'ListItem',
  components: { Checkbox, Input },
  props: {
    modelValue: {
      type: Object,
      default: {}
    },
    focus: {
      default: false
    }
  },
  methods: {
    onClick() {
      this.$emit('remove', this.modelValue)
    }
  }
}
</script>
