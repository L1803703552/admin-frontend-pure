<script setup lang="ts">
import { useWindowSize } from "@vueuse/core";
import { ref } from "vue";
const { width } = useWindowSize();
const selVal = ref([]);
const value = ref("阳澄湖北区");

// 默认数据
selVal.value = ["阳澄湖南区", "阳澄湖北区", "江宁南区", "江宁北区"];
</script>

<template>
  <el-text style="margin-right: 10px" v-if="width > 767">统计服务区</el-text>
  <el-select v-model="value" size="small" :fit-input-width="true">
    <el-option v-for="item in selVal" :key="item" :label="item" :value="item" />
  </el-select>
</template>
