<script setup lang="ts">
import { ref } from "vue";
import { defineProps } from "vue";
defineOptions({
  name: "ProgressLine"
});
const props = defineProps({
  label: {
    type: String,
    require: true
  },
  value: {
    type: Number,
    require: true
  },
  valueMax: {
    type: Number,
    require: true
  },
  status: {} as any
});
const per = ref(0);
const isIndet = ref(true);
setTimeout(() => {
  isIndet.value = false;
}, 800);
per.value = props.valueMax === 0 ? 0 : props.value / props.valueMax;
</script>

<template>
  <el-row :gutter="24" style="align-items: center; margin: 5px 0">
    <el-col :xs="6" :sm="4" :md="6" :lg="6" :xl="3" style="font-size: 12px">
      {{ props.label }}
    </el-col>
    <el-col :xs="18" :sm="20" :md="18" :lg="18" :xl="21">
      <el-progress
        :indeterminate="isIndet"
        :status="props.status"
        :percentage="per * 100"
      >
        <el-text>{{ props.value }}/{{ props.valueMax }}</el-text>
      </el-progress>
    </el-col>
  </el-row>
</template>

<style lang="scss" scoped></style>
