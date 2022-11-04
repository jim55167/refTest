<script setup>
import { ref, watchEffect } from "vue";

const testState = ref({
  notLogin: Number,
  totalPerson: Number,
  totalTicket: Number,
  done: Number,
});
const props = defineProps({
  obj: {
    type: Object,
    required: true
  }
});

function test() {
  const data = props.obj.data;
  console.log(data)

  //把下列的註解掉就不會噴錯
  const num = Array.from(
    new Set(
      data.map((item) => {
        return item.id;
      })
    )
  );
  testState.value.totalPerson = num.length;
  console.log(num.length); //78
}

watchEffect(() => {
  test();
});
</script>

<template>
  <div>{{testState.totalPerson}}</div>
</template>
