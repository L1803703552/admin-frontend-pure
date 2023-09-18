<script setup lang="ts">
import busSide from "@iconify-icons/mdi/bus-side";
import busDoubleDecker from "@iconify-icons/mdi/bus-double-decker";
import carEmergency from "@iconify-icons/mdi/car-emergency";
import carLiftedPickup from "@iconify-icons/mdi/car-lifted-pickup";
import { useWindowSize } from "@vueuse/core";

defineOptions({
  name: "Traffic"
});
const { width } = useWindowSize();
const col = width.value >= 768 ? 4 : 2;
</script>

<template>
  <el-descriptions
    title="今日入区（车次）"
    direction="vertical"
    :column="col"
    border
    size="small"
    class="mb-[2vh]"
  >
    <el-descriptions-item>
      <template #label>
        <div class="flex items-center gap-1">
          <el-icon style="font-size: 20px">
            <iconify-icon-offline :icon="busSide" />
          </el-icon>
          小客车
        </div>
      </template>
      1209
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="flex items-center gap-1">
          <el-icon style="font-size: 20px">
            <iconify-icon-offline :icon="busDoubleDecker" />
          </el-icon>
          大客车
        </div>
      </template>
      39
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="flex items-center gap-1">
          <el-icon style="font-size: 20px">
            <iconify-icon-offline :icon="carEmergency" />
          </el-icon>
          危化品
        </div>
      </template>
      15
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="flex items-center gap-1">
          <el-icon style="font-size: 20px">
            <iconify-icon-offline :icon="carLiftedPickup" />
          </el-icon>
          其他
        </div>
      </template>
      768
    </el-descriptions-item>
  </el-descriptions>
  <el-descriptions
    title="当前在区车辆（辆）"
    direction="vertical"
    :column="col"
    border
    size="small"
  >
    <el-descriptions-item>
      <template #label>
        <div class="flex items-center gap-1">
          <el-icon style="font-size: 20px">
            <iconify-icon-offline :icon="busSide" />
          </el-icon>
          小客车
        </div>
      </template>
      456
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="flex items-center gap-1">
          <el-icon style="font-size: 20px">
            <iconify-icon-offline :icon="busDoubleDecker" />
          </el-icon>
          大客车
        </div>
      </template>
      0
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="flex items-center gap-1">
          <el-icon style="font-size: 20px">
            <iconify-icon-offline :icon="carEmergency" />
          </el-icon>
          危化品
        </div>
      </template>
      2
    </el-descriptions-item>
    <el-descriptions-item>
      <template #label>
        <div class="flex items-center gap-1">
          <el-icon style="font-size: 20px">
            <iconify-icon-offline :icon="carLiftedPickup" />
          </el-icon>
          其他
        </div>
      </template>
      98
    </el-descriptions-item>
  </el-descriptions>
</template>

<style lang="scss" scoped></style>
