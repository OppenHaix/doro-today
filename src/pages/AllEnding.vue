<script lang="ts" setup>
// 所有结局页面
// 该页面展示所有结局的图片和描述
import router from "@/router";
import { reactive } from "vue";
import cards from "@/assets/cards.json"; // 引入卡片数据
const endings = reactive(cards);

const 返回抽卡页面 = () => {
  // 使用 Vue Router 跳转到抽卡页面
  router.push("/");
};
</script>
<template>
  <div class="home">
    <h1>所有结局</h1>
    <v-btn @click="返回抽卡页面()" class="v-btn">返回抽卡页面</v-btn>
    <div class="ending-list">
      <div class="ending-item" v-for="(ending, index) in endings" :key="index">
        <v-img :src="ending.image" class="v-image" />
        <h2>{{ ending.title }}</h2>
        <p>{{ ending.description }}</p>
      </div>
    </div>
  </div>
</template>

<style lang="css" scoped>
.home {
  color: black;
  font-family: "Roboto", sans-serif;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #f5f5f5;

  .v-btn {
    background-color: #ff4081;
    color: #fff;
    border-radius: 30px;
    padding: 5px 10px 5px 10px;
    margin: 10px;
    font-size: 16px;
    font-weight: bold;
    text-decoration: none;
    transition: background-color 0.3s;
  }

  .ending-list {
    display: flex;
    flex-wrap: wrap;
    /* justify-content: center; */
    /* align-items: center; */
    margin: 20px;

    .ending-item {
      margin: 10px;
      text-align: center;
      width: 200px;

      /* 设置每个结局项的宽度 */
      .v-image {
        width: 100%;
        height: auto;
        border-radius: 10px;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
      }

      p {
        margin-top: 5px;
        font-size: 14px;
        color: #333;
      }
    }
  }
}
</style>
