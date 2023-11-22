<script setup lang="ts">
import { onMounted, ref } from 'vue';
const joke = ref("");
const buttonName = "CHUCK ME!!!"


const getJoke = async () => {
  console.log("GETTING JOKE")
  const response = await fetch('https://api.chucknorris.io/jokes/random');
  const json = await response.json();
  joke.value = json.value;
}
onMounted(() => getJoke())

</script>
<template>
  <div class="pt-5">
    <p class="jokeContainer">{{ joke }}</p>
    <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" @click="getJoke()">
        {{ buttonName }}
      </button>

  </div>
</template>

<style>
  .jokeContainer {
    min-height: 100px;
  }
</style>

