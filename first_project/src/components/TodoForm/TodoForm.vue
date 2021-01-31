<template>
    <div class="form">
      <input placeholder="Todo" v-model="newItem" />
      <button @click="addItem">Add</button>
    </div>     
</template>

<script>
  export default {
    data(){
      return {
        newItem: ''
      }
    },
    props:['items'],
    methods: {
      addItem() {
        this.items.push({ 
            title: this.newItem, 
            completed: false, 
            id: Math.random()
        })
      }
    }
  }
</script>

<style>
    @import './todoForm.css';
</style>