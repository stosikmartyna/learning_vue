<template>
  <div class="container">
    <TodoForm 
        :items="items"
    />

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
    import TodoForm from '../TodoForm/TodoForm';
    import TodoItem from '../TodoItem/TodoItem';

    export default {
        components: {
            TodoForm,
            TodoItem
        },
        data() {
            return {
                items: [
                    { title: 'To water the plants', completed: false, id: 1 },
                    { title: 'Take out the trash', completed: true, id: 2 }
                ]
            }
        },
        methods: {
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