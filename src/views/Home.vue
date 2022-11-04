<script setup>
import { ref, inject, onMounted } from "vue";
import Child from "@/components/Child.vue";
const axios = inject("axios");

const testData = ref({})

onMounted(async () => {
  await axios
    .get("https://api.tvmaze.com/schedule?country=US&date=2014-12-01")
    .then((response) => {
      testData.value = response;
    })
    .catch((err) => {
      console.log("Error：" + err);
    });
}); 
</script>

<template>
  <div class="flex">
    <Child :obj="testData" />
  </div>
</template>
