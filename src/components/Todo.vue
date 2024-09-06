<script setup>
import { ref } from "vue";
const newTask = ref("");
const tasks = ref(["Initial Task"]);

// add task
const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};
// remove task
const removeTask = (index) => {
  tasks.value.splice(index, 1);
};
</script>

<template>
  <div
    class="w-full max-w-screen-sm mx-auto px-4 bg-slate-50 py-8 rounded-md border border-slate-200 grid gap-4"
  >
    <h1 class="text-3xl font-medium text-center text-emerald-600">Todo App</h1>
    <!-- add task section -->
    <div class="flex items-center justify-between gap-4">
      <input
        type="text"
        class="px-3 py-1.5 rounded-md border border-slate-200 focus-visible:border-emerald-500 focus-visible:outline-none text-sm font-medium w-full"
        placeholder="Enter your task"
        v-model="newTask"
        @keyup.enter="addTask"
      />
      <button
        @click="addTask"
        class="px-3 py-1.5 text-sm font-medium rounded-md bg-emerald-500 text-white shrink-0 disabled:opacity-50"
      >
        Add Task
      </button>
    </div>
    <!-- map all tasks -->
    <ul class="text-base font-medium grid gap-2">
      <li
        v-for="(task, index) in tasks"
        :key="index"
        class="flex items-center justify-between w-full gap-4"
      >
        <p class="px-3 py-1.5 bg-slate-100 rounded-md w-full">
          {{ index + 1 }}. {{ task }}
        </p>
        <button
          @click="removeTask(index)"
          class="px-3 py-1.5 text-sm font-medium rounded-md bg-rose-500 text-white shrink-0 disabled:opacity-50"
        >
          Remove
        </button>
      </li>
    </ul>
  </div>
</template>
