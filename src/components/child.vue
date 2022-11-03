<script setup>
import { ref, onMounted } from "vue";

const state = ref([]);

const props = defineProps({
  arr: {
    type: Array,
    required: true,
  },
});
// console.log(state)
// console.log(props)
// console.log(props.arr)

function getData() {
  const data = props.arr;
  // console.log(data)
  data.forEach((item) => {
    state.value.push({
      "score": item.score,
      "id": item.show.id,
      "name": item.show.name
    });
  });
}

getData();
</script>

<template>
  <div>
    <ul v-for="states in state" :key="state.score">
      <li>Name：{{states.name}}</li>
      <li>ID：{{states.id}}</li>
      <li>Score: {{states.score}}</li>
    </ul>
  </div>
</template>
