<script setup>
import Heading from '../typography/Heading.vue';
import TodoItem from './TodoItem.vue';
import TodoAdd from './TodoAdd.vue';
import { ref } from 'vue';

const todos = ref([
  { body: 'First', completed: false },
  { body: 'Second', completed: false },
  { body: 'Second', completed: false },
  { body: 'Second', completed: false },
])


const addTodo = (todo) => {
  todos.value = [...todos.value, todo]
}

const deleteTodo = (index) => {
  todos.value.splice(index, 1)
}

</script>

<template>
  <div class="mx-auto">
    <div class="text-center">
      <Heading>Vue Todo App</Heading>
      <p class="my-4">Just type something and click add...</p>
    </div>

    <div class="shadow-lg mt-8 max-w-lg mx-auto">
      <TodoItem v-for="todo in todos" :todo="todo" :index="index" @deleteTodo="deleteTodo"></TodoItem>
      <TodoAdd @addTodo="addTodo"></TodoAdd>
    </div>
  </div>
</template>
