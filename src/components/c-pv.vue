<template>
  <div>{{ data }}</div>
</template>
<script setup>
import { ref, inject } from "vue";
// const emits = defineEmits(["add"]);
// const props = defineProps({
//   msg: String,
// });
// defineExpose({ list });
const data = inject("provide-data");
</script>

<style scoped></style>
