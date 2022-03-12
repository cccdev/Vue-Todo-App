<script setup>
import { ref } from 'vue'

const emit = defineEmits()

const todoBody = ref('')
const todoBodyInput = ref(null)

const addTodo = () => {
  if (!todoBody.value) {
    return null
  }
  emit('addTodo', {
    body: todoBody.value,
    completed: false
  })
  todoBody.value = ''
  // todoBodyInput.value.focus()
}
</script>
<template>
  <div class>
    <div class="flex">
      <input
        v-model="todoBody"
        @keyup.enter="addTodo"
        class="w-full px-4 py-2 focus:outline-none"
        type="text"
      />
      <button
        @click="addTodo"
        class="px-8 py-2 bg-indigo-500 text-white hover:bg-indigo-600 transition ease-in-out"
      >Add</button>
    </div>
  </div>
</template>
