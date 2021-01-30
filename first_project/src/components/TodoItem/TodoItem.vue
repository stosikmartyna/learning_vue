<template>
  <div>
    <div 
      class="item" 
      v-bind:class="{
        item_completed: item.completed
      }" 
    >
      <span>{{ item.title }}</span>
      <button v-if="!item.completed" @click="selectItem">Done</button>
    </div>
  </div>
</template>

<script>
  export default {
      props: ['item'],
      methods: {
          selectItem() {
              this.$emit('selectedItem', this.item.id)
              // wysyłamy informacje do nadrzędnego komponentu
          }
      }
  }
</script>

<style scoped>
  @import './todoItem.css';
</style>