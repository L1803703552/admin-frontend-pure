<script setup lang="ts">
import Line from "./Line.vue";
import ProgressLine from "./ProgressLine.vue";
defineOptions({
  name: "ParkSpace"
});
</script>

<template>
  <h4>当前剩余</h4>
  <ProgressLine label="大型车" status="warning" :value="12" :value-max="25" />
  <ProgressLine label="小型车" :value="60" :value-max="110" />
  <ProgressLine label="危化品" status="exception" :value="3" :value-max="12" />
  <h4 class="mt-4">24小时车位使用率</h4>
  <Line />
</template>

<style lang="scss" scoped>
h4 {
  font-size: 14px;
}
</style>
