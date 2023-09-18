<script setup lang="ts">
import { ref } from "vue";
import TypeIt from "@/components/ReTypeit";
import Traffic from "./components/Traffic.vue";
import ParkSpace from "./components/ParkSpace.vue";
import Special from "./components/Special.vue";
import Passenger from "./components/Passenger.vue";
import Event from "./components/Event.vue";
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
          <el-card shadow="never" style="height: 37vh">
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
                <el-scrollbar height="27vh">
                  <Traffic />
                </el-scrollbar>
              </template>
            </el-skeleton>
          </el-card>
        </el-col>

        <!-- 剩余车位 -->
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
          <el-card shadow="never" style="height: 47vh">
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
                <el-scrollbar height="35vh">
                  <ParkSpace />
                </el-scrollbar>
              </template>
            </el-skeleton>
          </el-card>
        </el-col>
      </el-col>

      <el-col :xs="24" :sm="24" :md="8" :lg="8" :xl="8" style="padding: 0">
        <!-- 特殊车辆 -->
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
                  <Special />
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
          <el-card shadow="never" style="height: 47vh">
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
                <el-scrollbar height="39vh">
                  <Passenger />
                </el-scrollbar>
              </template>
            </el-skeleton>
          </el-card>
        </el-col>

        <!-- 事件 -->
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
          <el-card shadow="never" style="height: 37vh">
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
                <el-scrollbar height="29vh">
                  <Event />
                </el-scrollbar>
              </template>
            </el-skeleton>
          </el-card>
        </el-col>
      </el-col>
    </el-row>
  </div>
</template>
<style lang="scss" scoped></style>
