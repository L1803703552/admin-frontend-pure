<script setup lang="ts">
import { ref } from "vue";
import TypeIt from "@/components/ReTypeit";
import Line from "./components/Line.vue";
import { ReboundCountTo } from "@/components/ReCountTo";
defineOptions({
  name: "Welcome"
});

const loading = ref<boolean>(true);

setTimeout(() => {
  loading.value = !loading.value;
}, 800);
</script>

<template>
  <div>
    <el-row :gutter="24">
      <el-col :xs="24" :sm="24" :md="8" :lg="8" :xl="8" style="padding: 0">
        <!-- 车流量 -->
        <el-col
          class="mb-[2vh]"
          v-motion
          :initial="{
            opacity: 0,
            y: 100
          }"
          :enter="{
            opacity: 1,
            y: 0,
            transition: {
              delay: 200
            }
          }"
        >
          <el-card shadow="never" style="height: 42vh">
            <template #header>
              <TypeIt
                :className="'type-it2'"
                :values="[`车流量`]"
                :cursor="false"
                :speed="60"
              />
            </template>
            <el-skeleton animated :rows="6" :loading="loading">
              <template #default>
                <el-scrollbar height="30vh">
                  <el-descriptions
                    title="今日入区（车次）"
                    direction="vertical"
                    :column="2"
                    border
                    size="small"
                    class="mb-[2vh]"
                  >
                    <el-descriptions-item label="小客车"
                      >1208</el-descriptions-item
                    >
                    <el-descriptions-item label="大客车"
                      >39</el-descriptions-item
                    >
                    <el-descriptions-item label="危化品"
                      >15</el-descriptions-item
                    >
                    <el-descriptions-item label="其他"
                      >768</el-descriptions-item
                    >
                  </el-descriptions>
                  <el-descriptions
                    title="当前在区车辆（辆）"
                    direction="vertical"
                    :column="2"
                    border
                    size="small"
                  >
                    <el-descriptions-item label="小客车"
                      >456</el-descriptions-item
                    >
                    <el-descriptions-item label="大客车"
                      >0</el-descriptions-item
                    >
                    <el-descriptions-item label="危化品"
                      >2</el-descriptions-item
                    >
                    <el-descriptions-item label="其他">98</el-descriptions-item>
                  </el-descriptions>
                </el-scrollbar>
              </template>
            </el-skeleton>
          </el-card>
        </el-col>

        <!-- 剩余车位 -->
        <el-col
          v-motion
          :initial="{
            opacity: 0,
            y: 100
          }"
          :enter="{
            opacity: 1,
            y: 0,
            transition: {
              delay: 400
            }
          }"
        >
          <el-card shadow="never" style="height: 42vh">
            <template #header>
              <TypeIt
                :className="'type-it3'"
                :values="['剩余车位']"
                :cursor="false"
                :speed="120"
              />
            </template>
            <el-skeleton animated :rows="6" :loading="loading">
              <template #default>
                <el-scrollbar height="30vh">
                  <h4>当前剩余</h4>
                  <el-row
                    :gutter="24"
                    style="align-items: center; margin: 5px 0"
                  >
                    <el-col :span="3" style="font-size: 12px"> 大型车 </el-col>
                    <el-col :span="21">
                      <el-progress :percentage="200 / 25">
                        <el-text>2/25</el-text>
                      </el-progress>
                    </el-col>
                  </el-row>
                  <el-row
                    :gutter="24"
                    style="align-items: center; margin: 5px 0"
                  >
                    <el-col :span="3" style="font-size: 12px"> 小型车 </el-col>
                    <el-col :span="21">
                      <el-progress :percentage="0 / 110">
                        <el-text>0/110</el-text>
                      </el-progress>
                    </el-col>
                  </el-row>
                  <el-row
                    :gutter="24"
                    style="align-items: center; margin: 5px 0"
                  >
                    <el-col :span="3" style="font-size: 12px"> 危化品 </el-col>
                    <el-col :span="21">
                      <el-progress :percentage="0">
                        <el-text>0/0</el-text>
                      </el-progress>
                    </el-col>
                  </el-row>
                  <h4>24小时车位使用率</h4>
                  <Line />
                </el-scrollbar>
              </template>
            </el-skeleton>
          </el-card>
        </el-col>
      </el-col>

      <el-col :xs="24" :sm="24" :md="8" :lg="8" :xl="8" style="padding: 0">
        <!-- 特殊车辆 -->
        <el-col
          v-motion
          :initial="{
            opacity: 0,
            y: 100
          }"
          :enter="{
            opacity: 1,
            y: 0,
            transition: {
              delay: 200
            }
          }"
        >
          <el-card shadow="never" style="height: 86vh">
            <template #header>
              <TypeIt
                :className="'type-it1'"
                :values="['特殊车辆']"
                :cursor="false"
                :speed="120"
              />
            </template>
            <el-skeleton animated :rows="13" :loading="loading">
              <template #default>
                <el-scrollbar height="75vh">
                  <div>
                    <el-descriptions
                      title="危化品"
                      direction="vertical"
                      :column="1"
                      size="small"
                    >
                      <el-descriptions-item label="今日入园（车次）">
                        <ul class="flex">
                          <ReboundCountTo
                            v-for="(num, inx) of [0, 0, 0, 0, 1, 5]"
                            :key="inx"
                            :i="num"
                            :blur="inx"
                            :delay="inx / 2"
                          />
                        </ul>
                      </el-descriptions-item>
                      <el-descriptions-item label="当前在区车辆（辆）" />
                    </el-descriptions>
                    <el-descriptions :column="3" size="small">
                      <el-descriptions-item label="等待登记">
                        0
                      </el-descriptions-item>
                      <el-descriptions-item label="等待巡查">
                        0
                      </el-descriptions-item>
                      <el-descriptions-item label="停留超时">
                        0
                      </el-descriptions-item>
                      <el-descriptions-item label="24小时车次统计" :span="3">
                        <Line />
                      </el-descriptions-item>
                    </el-descriptions>
                  </div>
                  <div>
                    <el-descriptions
                      title="新能源"
                      direction="vertical"
                      :column="1"
                      size="small"
                    >
                      <el-descriptions-item label="今日入园（车次）">
                        <ul class="flex">
                          <ReboundCountTo
                            v-for="(num, inx) of [0, 0, 0, 1, 2, 7]"
                            :key="inx"
                            :i="num"
                            :blur="inx"
                            :delay="inx / 2"
                          />
                        </ul>
                      </el-descriptions-item>
                      <el-descriptions-item label="当前在区车辆（辆）" />
                    </el-descriptions>
                    <el-descriptions :column="3" size="small">
                      <el-descriptions-item label="小客车">
                        35
                      </el-descriptions-item>
                      <el-descriptions-item label="大客车">
                        0
                      </el-descriptions-item>
                      <el-descriptions-item label="其他">
                        0
                      </el-descriptions-item>
                      <el-descriptions-item label="24小时车次统计" :span="3">
                        <Line />
                      </el-descriptions-item>
                    </el-descriptions>
                  </div>
                </el-scrollbar>
              </template>
            </el-skeleton>
          </el-card>
        </el-col>
      </el-col>

      <el-col :xs="24" :sm="24" :md="8" :lg="8" :xl="8" style="padding: 0">
        <!-- 客流量 -->
        <el-col
          class="mb-[2vh]"
          v-motion
          :initial="{
            opacity: 0,
            y: 100
          }"
          :enter="{
            opacity: 1,
            y: 0,
            transition: {
              delay: 400
            }
          }"
        >
          <el-card shadow="never" style="height: 42vh">
            <template #header>
              <TypeIt
                :className="'type-it4'"
                :values="['客流量']"
                :cursor="false"
                :speed="120"
              />
            </template>
            <el-skeleton animated :rows="6" :loading="loading">
              <template #default>
                <el-scrollbar height="30vh">
                  <el-descriptions
                    title="今日入区（人次）"
                    direction="vertical"
                    :column="3"
                    size="small"
                  >
                    <el-descriptions-item label="主楼">
                      0
                    </el-descriptions-item>
                    <el-descriptions-item label="女卫">
                      0
                    </el-descriptions-item>
                    <el-descriptions-item label="男卫">
                      0
                    </el-descriptions-item>
                    <el-descriptions-item label="24小时车次统计" :span="3">
                      <Line />
                    </el-descriptions-item>
                  </el-descriptions>
                </el-scrollbar>
              </template>
            </el-skeleton>
          </el-card>
        </el-col>

        <!-- 事件 -->
        <el-col
          v-motion
          :initial="{
            opacity: 0,
            y: 100
          }"
          :enter="{
            opacity: 1,
            y: 0,
            transition: {
              delay: 400
            }
          }"
        >
          <el-card shadow="never" style="height: 42vh">
            <template #header>
              <TypeIt
                :className="'type-it5'"
                :values="['事件']"
                :cursor="false"
                :speed="120"
              />
            </template>
            <el-skeleton animated :rows="6" :loading="loading">
              <template #default>
                <el-scrollbar height="30vh">
                  <el-empty :image-size="120" />
                </el-scrollbar>
              </template>
            </el-skeleton>
          </el-card>
        </el-col>
      </el-col>
    </el-row>
  </div>
</template>
<style lang="scss" scoped>
h4 {
  font-size: 14px;
}
</style>
