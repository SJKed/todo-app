<template>
  <div class="todoList">
    <TodoItem v-for="item in todos" :key="item.id" :todos="item" @delete="$emit('delete', item)" @checked="$emit('checked', item)"/>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue'
export default {
    components: {
        TodoItem,
    },
    props: ['todos'],
}
</script>

<style>
.todoList {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}


</style>
