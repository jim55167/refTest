<script setup>
import { ref, inject, onMounted } from "vue";
import child from "@/components/child.vue";
const axios = inject('axios')

const resData = ref([]);

onMounted(async () => {
  await axios.get("https://api.tvmaze.com/search/shows?q=girls")
    .then(res => {
      resData.value = res.data
    })
    .catch(err => {
      console.log("Error：" + err);
    })
})

</script>

<template>
  <div>
    <child :arr="resData" />
  </div>
</template>
