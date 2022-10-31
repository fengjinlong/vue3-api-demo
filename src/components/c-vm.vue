<template>
  <div>child--{{ props.modelValue }}</div>
  <button @click="btn">change-v-model</button>
</template>
<script setup>
import { ref } from "vue";
// const emits = defineEmits(["add"]);
// const props = defineProps({
//   msg: String,
// });
// defineExpose({ list });
const emits = defineEmits(["update:modelValue"]);
const props = defineProps({
  modelValue: String,
});
const btn = () => {
  emits("update:modelValue", "update-v-modelValue");
};
</script>

<style scoped></style>
