<script setup>
import { ref, onMounted } from "vue";
const quotes = ref([
  {
    text: "The only way to do great work is to love what you do.",
    author: "Steve Jobs",
  },
  {
    text: "Success is not the key to happiness. Happiness is the key to success.",
    author: "Albert Schweitzer",
  },
  {
    text: "In the middle of difficulty lies opportunity.",
    author: "Albert Einstein",
  },
  {
    text: "Life is 10% what happens to us and 90% how we react to it.",
    author: "Charles R. Swindoll",
  },
  {
    text: "Do not go where the path may lead, go instead where there is no path and leave a trail.",
    author: "Ralph Waldo Emerson",
  },
]);

const currentQuote = ref({ text: "", author: "" });

const getRandomQuote = () => {
  const randomIndex = Math.floor(Math.random() * quotes.value.length);
  currentQuote.value = quotes.value[randomIndex];
  console.log("randomQuote", randomIndex);
  
};

onMounted(() => {
  getRandomQuote();
});
</script>

<template>
  <div class="w-full max-w-screen-sm mx-auto px-4 bg-slate-50 py-8 rounded-md grid place-items-center gap-4 border border-slate-200">
    <h1 class="text-3xl font-medium text-center text-emerald-600">
      Random Quote Generator
    </h1>

    <p class="text-center text-sm font-medium">
      <span>{{ currentQuote.text }}</span>
      <br />
      <span class="text-sm text-gray-600"> — {{ currentQuote.author }} </span>
    </p>

    <button
      @click="getRandomQuote"
      class="px-3 py-1.5 text-sm font-medium rounded-md bg-emerald-500 text-white shrink-0 disabled:opacity-50"
    >
      Generate random quote
    </button>
  </div>
</template>
