<template>
  <div
    class="min-h-screen flex flex-col items-center justify-center bg-gray-100"
  >
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Task Manager</h1>

    <div class="w-[400px] mx-auto rounded-md border p-4 space-y-4 bg-white">
      <div class="border-b border-gray-200 pb-4 mb-4">
        <div class="flex flex-col items-center md:flex-row md:items-stretch">
          <input
            v-model="task"
            type="text"
            name="name"
            id="name"
            class="w-full md:w-2/3 rounded-md border-gray-300 focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm mb-2 md:mb-0 md:mr-2 p-2"
            placeholder="Add a task"
          />
          <button
            :disabled="!task"
            @click="addTask"
            type="button"
            class="w-full md:w-1/3 bg-indigo-600 text-white px-4 py-2 rounded-md transition-all duration-300 ease-in-out hover:bg-indigo-700 focus:outline-none focus:ring focus:border-indigo-300"
          >
            Add
          </button>
        </div>
      </div>

      <div class="flex flex-col md:flex-row items-start justify-between">
        <div class="w-full md:w-3/4">
          <div v-for="todo in taskForm" :key="todo" class="mb-2">
            <div class="flex items-center">
              <span class="mr-2 text-indigo-500">&#8226;</span>
              <!-- Bullet point or icon -->
              <p class="text-sm text-gray-500">{{ todo }}</p>
            </div>
          </div>
        </div>

        <div class="w-full md:w-1/4 ml-0 md:ml-4"></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const taskForm = ref([]);
const task = ref("");

const addTask = () => {
  taskForm.value.push(task.value);
  task.value = "";
};
</script>

<style scoped>
/* Add any custom styles specific to this component */
</style>
