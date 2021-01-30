<template>
  <div class="container">
    <div class="form">
      <input placeholder="Todo" v-model="newItem"/>
      <button @click="addItem">Add</button>
    </div>

    <div 
      class="item" 
      v-bind:class="{
        item_completed: item.completed
      }" 
      v-for="item in items" 
      v-bind:key="item.id"
    >
      <span>{{ item.title }}</span>
      <button v-if="!item.completed" @click="selectItem(item.id)">Done</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: '',
      items: [
        { title: 'To water the plants', completed: false, id: 1 },
        { title: 'Take out the trash', completed: true, id: 2 }
      ]
    }
  },
  methods: {
    addItem() {
      this.items.push({ 
        title: this.newItem, 
        completed: false, 
        id: Math.random()
      })
    this.newItem = ''
    },
    selectItem(id) {
      const index = this.items.findIndex(el => el.id === id)
      this.items[index].completed = true
    }
  }
}
</script>

<style>
  .container {
    margin: 0 auto;
    width: 250px;
  }

  .form {
    display: flex;
    justify-content: space-between;
    margin-bottom: 1rem;
  }

  .item {
    border: 1px solid grey;
    display: flex;
    justify-content: space-between;
    margin-bottom: .5rem;
    padding: 10px;
  }

  .item_completed {
    opacity: 0.5;
  }

  .item_completed span {
    text-decoration: line-through;
  }
</style>