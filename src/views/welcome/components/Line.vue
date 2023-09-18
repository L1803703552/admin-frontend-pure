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
  for (let i = 0; i < 24; i++) {
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
    right: "10px",
    left: "30px"
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
      symbolSize: 5,
      symbol: "circle",
      smooth: true,
      data: [
        39, 36, 99, 27, 5, 54, 88, 10, 28, 40, 50, 96, 38, 41, 59, 79, 12, 97,
        42, 83, 77, 14, 75, 32
      ]
    },
    {
      name: "大客车",
      type: "line",
      symbolSize: 5,
      symbol: "circle",
      smooth: true,
      data: [
        65, 42, 53, 43, 20, 84, 78, 91, 70, 7, 9, 83, 4, 96, 2, 72, 88, 56, 58,
        19, 76, 13, 32, 30
      ]
    },
    {
      name: "危化品",
      type: "line",
      symbolSize: 5,
      symbol: "circle",
      smooth: true,
      data: [
        9, 37, 15, 93, 44, 22, 25, 10, 68, 56, 99, 63, 62, 50, 67, 75, 88, 49,
        55, 94, 85, 91, 100, 70
      ]
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
  <div ref="lineChartRef" style="width: 100%; height: 180px" />
</template>
