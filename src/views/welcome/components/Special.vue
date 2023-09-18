<script setup lang="ts">
import Line from "./Line.vue";
import { ReboundCountTo } from "@/components/ReCountTo";
defineOptions({
  name: "Special"
});
</script>

<template>
  <el-descriptions title="危化品" direction="vertical" :column="1" size="small">
    <el-descriptions-item label="今日入园（车次）">
      <ul class="flex">
        <ReboundCountTo
          v-for="(num, inx) of [0, 0, 0, 0, 1, 5]"
          :key="inx"
          :i="num"
          :blur="inx"
          :delay="inx / 4"
        />
      </ul>
    </el-descriptions-item>
  </el-descriptions>
  <el-descriptions direction="vertical" :column="3">
    <el-descriptions-item :span="3" label="当前在区车辆（辆）" />
    <el-descriptions-item label="等待登记"> 0 </el-descriptions-item>
    <el-descriptions-item label="等待巡查"> 0 </el-descriptions-item>
    <el-descriptions-item label="停留超时"> 0 </el-descriptions-item>
    <el-descriptions-item label="24小时车次统计" :span="3">
      <Line />
    </el-descriptions-item>
  </el-descriptions>
  <el-descriptions title="新能源" direction="vertical" :column="1" size="small">
    <el-descriptions-item label="今日入园（车次）">
      <ul class="flex">
        <ReboundCountTo
          v-for="(num, inx) of [0, 0, 0, 1, 2, 7]"
          :key="inx"
          :i="num"
          :blur="inx"
          :delay="inx / 4"
        />
      </ul>
    </el-descriptions-item>
  </el-descriptions>
  <el-descriptions direction="vertical" :column="3">
    <el-descriptions-item :span="3" label="当前在区车辆（辆）" />
    <el-descriptions-item label="小客车"> 35 </el-descriptions-item>
    <el-descriptions-item label="大客车"> 0 </el-descriptions-item>
    <el-descriptions-item label="其他"> 0 </el-descriptions-item>
    <el-descriptions-item label="24小时车次统计" :span="3">
      <Line />
    </el-descriptions-item>
  </el-descriptions>
</template>

<style lang="scss" scoped></style>
