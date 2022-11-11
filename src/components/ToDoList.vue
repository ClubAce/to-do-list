<template>
  <div class="container">
    <div class="card">
      <Input class="title" v-model="title" @input="updateList('title')" placeholder="Ny opgaveliste" />
      <List v-model="list" @input="updateList('list')" @remove="removeItem" :focus="focus" />
      <div class="card__footer">
        <button class="button button-icon button-sticky button-rounded" @click="addItem">
          <span class="button__text">Tilføj en opgave</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import List from './blocks/List.vue'
import Input from './snippets/Input.vue'
export default {
  name: 'ToDoList',
  components: { List, Input },
  data() {
    return {
      title: this.getStorage('title') || '',
      list: this.getStorage('list') || [],
      focus: -1,
      item: {},
      id: 1
    }
  },
  created() {
    if (!this.list.length) {
      return this.addItem()
    }
    this.id = this.getHeighestId()
  },
  methods: {
    addItem() {
      this.item = {id: this.id, done: false, task: ''}
      this.list.unshift(this.item)
      this.setStorage('list')
      this.focus = 0
      this.item = {}
      this.id++
    },
    removeItem(item) {
      this.list = this.list.filter(task => task.id != item.id)
      this.setStorage('list')
    },
    updateList(key = '') {
      this.setStorage(key)
    },
    getStorage(key = '') {
      return JSON.parse(localStorage.getItem(key))
    },
    setStorage(key = '') {
      localStorage.setItem(key, JSON.stringify(this[key]))
    },
    getHeighestId() {
      return this.list.reduce((previous, current) => {
        return previous.id > current.id ? previous : current
      }).id + 1
    }
  }
}
</script>
