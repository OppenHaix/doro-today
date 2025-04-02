<script lang="ts" setup>
// import Home from "@/components/AllEnding.vue";
import router from "@/router";
import { reactive } from "vue";

const state = reactive({
  图片: {
    图片地址: "/public/ending/bad_ending.jpeg",
    图片描述: "示例图片",
  },
});
const 跳转到所有结局页面 = () => {
  router.push("/allending"); // 使用 Vue Router 跳转到所有结局页面
};
</script>

<template>
  <div class="index">
    <h1>今天Doro是什么结局</h1>
    <!-- <Home /> -->
    <div class="buttons">
      <v-btn id="btn-left" class="v-btn"> 随机抽 </v-btn>
      <v-btn class="v-btn" @click="跳转到所有结局页面()"> 所有结局 </v-btn>
    </div>
    <v-img class="v-image" cover :src="state.图片.图片地址" />
  </div>
</template>
<style lang="css" scoped>
.index {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  /* height: 100vh; */
  font-family: "Roboto", sans-serif;
  color: #000;

  .buttons {
    .v-btn {
      background-color: #f5f5f5;
      color: #000;
      border-radius: 30px;
      padding: 5px 10px 5px 10px;
      margin: 10px;
      font-size: 16px;
      font-weight: bold;
      text-decoration: none;
      transition: background-color 0.3s;
    }
    #btn-left {
      background-color: #ff4081;
      color: #fff;
    }
  }

  .v-image {
    /* margin: 1rem 1rem 0 1rem; */
    text-align: center;
    display: block;
    height: 80%;
    width: 80%;
    max-width: 600px;
    max-height: 1000px;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    transition: transform 0.2s;
  }
}
</style>
