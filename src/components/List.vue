<script setup>
import useTodos from "../composables/useTodos";

const {pending, completed, changeStatus} = useTodos();

defineProps({
    isCompleted:{
        defalut: false,
        type: Boolean,
    },
});
</script>

<template>
     <div class="w-1/3">
          <h3 class="text-2xl text-center" :class="isCompleted ? 'text-green-500' : 'text-red-800'">{{isCompleted ? "Completed" : "Pending"}}</h3>
          <ul class="pt-8 space-y-4">
            <li
              v-for="todo in isCompleted ? completed : pending"
              :key="todo.id"
              @click="changeStatus(todo.id)"
              :class="isCompleted ? 'text-green-500 hover:bg-green-300' : 'text-red-500 hover:bg-red-300'"
              class="w-full px-4 py-2 font-bold text-center transition-colors duration-500 bg-gray-300 rounded-lg hover:cursor-pointer hover:text-gray-200"
            >
              {{ todo.content }}
            </li>
          </ul>
        </div>
</template>