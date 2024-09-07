<script setup>
import { ref } from "vue";

// Initial list of numbers
const initialNums = [0, 1, 2, 3, 4, 5, 6];
const nums = ref([...initialNums]); // Copy the initial array
const lodoNumber = ref(null);

const generateLodoNumber = () => {
  if (nums.value.length === 0) {
    nums.value = [...initialNums];
  }
  const randomIndex = Math.floor(Math.random() * nums.value.length);
  lodoNumber.value = nums.value[randomIndex];
  nums.value.splice(randomIndex, 1);
};
</script>

<template>
  <div
    class="w-full max-w-screen-sm mx-auto px-4 bg-slate-50 py-8 rounded-md grid place-items-center gap-4 border border-slate-200"
  >
    <h1 class="text-3xl font-medium text-center text-emerald-600">Lodo King</h1>

    <p class="text-center text-sm font-medium">{{ lodoNumber === null ? "No number yet" : lodoNumber }}</p>

    <button
      @click="generateLodoNumber"
      class="px-3 py-1.5 text-sm font-medium rounded-md bg-emerald-500 text-white shrink-0 disabled:opacity-50"
    >
      Press the button
    </button>
  </div>
</template>
