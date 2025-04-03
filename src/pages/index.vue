<script lang="ts" setup>
import router from "@/router";
import { reactive } from "vue";

import cards from "@/assets/cards.json"; // 引入卡片数据

const state = reactive({
  图片: cards[0], // 初始化为数组中的第一张图片
  是否显示图片: false, // 控制图片的显示
});

const 随机抽 = () => {
  if (!state.是否显示图片) {
    state.是否显示图片 = true; // 显示图片
  }
  state.图片 = cards[Math.floor(Math.random() * cards.length)]; // 随机选择一张图片
};

const 保存图片 = () => {
  const link = document.createElement("a");
  link.href = state.图片.image; // 获取图片的 URL
  link.download = `${state.图片.title}.png`; // 设置下载的文件名
  document.body.appendChild(link);
  link.click(); // 模拟点击下载
  document.body.removeChild(link); // 移除链接元素
};

const 跳转到所有结局页面 = () => {
  router.push("/allending"); // 使用 Vue Router 跳转到所有结局页面
};
</script>

<template>
  <div class="index">
    <h1>今天Doro是什么结局</h1>
    <div class="buttons">
      <v-btn id="btn-left" @click="随机抽()" class="v-btn"> 随机抽 </v-btn>
      <v-btn class="v-btn" @click="跳转到所有结局页面()"> 所有结局 </v-btn>
      <v-btn class="v-btn" v-show="state.是否显示图片" @click="保存图片()" id="btn-save">
        保存
      </v-btn>
    </div>
    <v-img v-show="state.是否显示图片" class="v-image" cover :src="state.图片.image" />
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
    #btn-save {
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
