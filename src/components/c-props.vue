<template>
  <div>{{ props.msg }}</div>
</template>
<script setup>
import { ref } from "vue";
// const emits = defineEmits(["add"]);
// const props = defineProps({
//   msg: String,
// });
// defineExpose({ list });
const props = defineProps({
  msg: String,
});
</script>

<style scoped></style>
