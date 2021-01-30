<template>
  <div class="container">
    <div class="form">
      <input placeholder="Todo" v-model="newItem"/>
      <button @click="addItem">Add</button>
    </div>     

    <TodoItem 
        v-for="item in items" 
        v-bind:key="item.id"
        :item="item"
        @selectedItem="selectItem"
    />

    <!-- v:bind:item="" or :item -->
    <!-- v-on:selectedItem="" or @selectedItem -->

  </div>
</template>

<script>
    import TodoItem from '../TodoItem/TodoItem';

    export default {
        components: {
            TodoItem
        },
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
    @import './todoView.css';
</style>