<script setup>
const emit = defineEmits()

defineProps({
  index: {
    type: Number,
    required: true,
  },
  todo: {
    body: {
      type: String,
      required: true,
    },
    completed: {
      type: Boolean,
      required: true,
    }
  }
})

const deleteTodo = (index) => {
  emit('deleteTodo', index)
}

const todoComplete = (todo) => {
  todo.completed = !todo.completed
}
</script>


<template>
  <div
    @click.stop="todoComplete(todo)"
    class="px-4 py-2 border-b flex hover:bg-indigo-50"
    :class="{
      'bg-gray-100': todo.completed,
      'text-gray-400': todo.completed,
      'line-through': todo.completed,
    }"
  >
    <div>{{ todo.body }}</div>
    <div class="ml-auto">
      <button
        @click="deleteTodo"
        class="item-center justify-center text-gray-300 hover:text-gray-500"
      >
        <span class="sr-only">Delete</span>
        <svg
          class="h-6 w-6"
          xmlns="http://www,w3.org/2000/svg"
          fill="none"
          stroke="currentColor"
          aria-hidden="true"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M6 18L18 6M6 6l12 12"
          />
        </svg>
      </button>
    </div>
  </div>
</template>
