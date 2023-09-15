<script setup lang="ts">
import { ref, computed, watch, type Ref } from "vue";
import {
  delay,
  useDark,
  useECharts,
  type EchartOptions
} from "@pureadmin/utils";
import { useAppStoreHook } from "@/store/modules/app";

const { isDark } = useDark();

const theme: EchartOptions["theme"] = computed(() => {
  return isDark.value ? "dark" : "default";
});

const lineChartRef = ref<HTMLDivElement | null>(null);
const { setOptions, resize } = useECharts(lineChartRef as Ref<HTMLDivElement>, {
  theme
});

const xData = (() => {
  const data: any[] = [];
  for (let i = 0; i < 24; i += 2) {
    data.push(`${i}时`);
  }
  return data;
})();

setOptions({
  tooltip: {
    trigger: "axis",
    axisPointer: {
      type: "shadow"
    }
  },
  grid: {
    bottom: "20px",
    right: "10px"
  },
  legend: {
    //@ts-expect-error
    right: true
  },
  calculable: true,
  xAxis: [
    {
      triggerEvent: true,
      type: "category",
      splitLine: {
        show: false
      },
      axisTick: {
        show: false
      },
      data: xData
    }
  ],
  yAxis: [
    {
      triggerEvent: true,
      type: "value",
      axisLine: {
        show: true
      }
    }
  ],
  series: [
    {
      name: "小型车",
      type: "line",
      smooth: true,
      data: [15, 8, 24, 16, 35, 4, 14, 18]
    },
    {
      name: "大客车",
      type: "line",
      smooth: true,
      data: [50, 86, 35, 47, 3, 37, 45, 22]
    },
    {
      name: "危化品",
      type: "line",
      smooth: true,
      data: [5, 87, 38, 4, 30, 7, 77, 2]
    }
  ],
  addTooltip: true
});

watch(
  () => useAppStoreHook().getSidebarStatus,
  () => {
    delay(600).then(() => resize());
  }
);
</script>

<template>
  <div ref="lineChartRef" style="width: 100%; height: 25vh" />
</template>
