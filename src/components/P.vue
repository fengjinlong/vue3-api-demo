<template>
  <div v-for="c in refc" :key="c">refc{{ c }}</div>
  <c-ref ref="refc" />
  <c-props msg="props-data" />
  <c-emit @emit="emit" />
  <c-pv />
  <c-vm v-model="modleVal" />
  <div>parent--{{ modleVal }}</div>
</template>
<script setup>
import { ref, provide } from "vue";
import cRef from "./c-ref.vue";
import cProps from "./c-props.vue";
import cEmit from "./c-emit.vue";
import cPv from "./c-pv.vue";
import cVm from "./c-vm.vue";
provide("provide-data", "provide-data");
// const emits = defineEmits(["add"]);
// const props = defineProps({
//   msg: String,
// });
const refc = ref(null);
const emit = (data) => {
  alert(data);
};
const modleVal = ref("modleVal");
</script>

<style scoped></style>
