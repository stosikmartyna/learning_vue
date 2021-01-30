<template>
  <div>
    <input placeholder="Todo" v-model="newItem"/>
    <button @click="addItem">Add</button>
    <div>
      <div v-for="item in items" v-bind:key="item.id">
        <span>{{ item.title }}</span>
      </div>
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
    }
  }
}
</script>