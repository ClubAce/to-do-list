<template>
  <div class="container">
    <div class="card">
      <Editable class="title" v-model="title" placeholder="Ny opgaveliste" />
      <List v-model="list">
        <ListItem v-if="Object.keys(item).length" v-model="item" @blur="onBlur" focus="true" />
      </List>
      <div class="card__footer">
        <button class="button button-icon button-sticky button-rounded" @click="addListItem">
          <span class="button__text">Tilføj ny opgave</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import List from './blocks/List.vue'
import ListItem from './blocks/ListItem.vue'
import Editable from './snippets/Editable.vue'
export default {
  name: 'ToDoList',
  components: { List, ListItem, Editable },
  data() {
    return {
      title: '',
      item: {},
      list: []
    }
  },
  created() {
    this.addListItem();
  },
  methods: {
    addListItem() {
      this.item = {checked: false, text: ''}
    },
    onBlur() {
      this.list.unshift(this.item)
      this.item = {}
    }
  }
}
</script>
