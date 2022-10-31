<template>
  <button @click="click">emits data</button>
</template>
<script setup>
// const emits = defineEmits(["add"]);
// const props = defineProps({
//   msg: String,
// });
// defineExpose({ list });
const emits = defineEmits(["emit"]);
const click = () => {
  emits("emit", "emit data");
};
</script>

<style scoped></style>
