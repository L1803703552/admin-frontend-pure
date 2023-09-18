<script setup lang="ts">
import Line from "./Line.vue";
import officeBuilding from "@iconify-icons/mdi/office-building";
import baselineMan from "@iconify-icons/ic/baseline-man";
import baselineWoman from "@iconify-icons/ic/baseline-woman";
defineOptions({
  name: "Passenger"
});
</script>

<template>
  <el-descriptions
    title="今日入区（人次）"
    direction="vertical"
    :column="3"
    size="small"
    border
  >
    <el-descriptions-item>
      <template #label>
        <div class="flex items-center gap-1">
          <el-icon style="font-size: 20px">
            <iconify-icon-offline :icon="officeBuilding" />
          </el-icon>
          主楼
        </div>
      </template>
      0
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="flex items-center gap-1">
          <el-icon style="font-size: 20px">
            <iconify-icon-offline :icon="baselineMan" />
          </el-icon>
          男卫
        </div>
      </template>
      0
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="flex items-center gap-1">
          <el-icon style="font-size: 20px">
            <iconify-icon-offline :icon="baselineWoman" />
          </el-icon>
          女卫
        </div>
      </template>
      0
    </el-descriptions-item>
  </el-descriptions>
  <el-descriptions direction="vertical" :column="1" class="mt-2">
    <el-descriptions-item label="24小时入区人次趋势">
      <Line />
    </el-descriptions-item>
  </el-descriptions>
</template>

<style lang="scss" scoped></style>
