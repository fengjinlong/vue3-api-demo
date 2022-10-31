<template></template>
<script setup>
import { reactive, ref } from "vue";
// const emits = defineEmits(["add"]);
// const props = defineProps({
//   msg: String,
// });
const list = reactive([1, 1]);
defineExpose(list);
</script>

<style scoped></style>
