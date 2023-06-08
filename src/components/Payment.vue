<script setup lang="ts">
const item1 = { name: "Desk", price: 300 };
const item2 = { name: "Bike", price: 500 };

const url = "https://www.yahoo.co.jp";

const buy = (itemName: string) => {
  alert(itemName + "を購入しますか？");
};
</script>

<template>
  <div class="container">
    <h1>最近の支出</h1>
    <div class="payment">
      <label>{{ item1.name }}</label>
      <label>{{ item1.price }}円</label>
      <a v-bind:href="url">bought at...</a>
      <button v-on:click="buy(item1.name)">buy</button>
    </div>
    <div class="payment">
      <label>{{ item2.name }}</label>
      <label>{{ item2.price }}円</label>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
}
.payment {
  display: flex;
  width: 400px;
  align-items: center;
  justify-content: space-between;
  height: 80px;
  margin-top: 60px;
  background: rgb(189, 207, 244);
  padding: 10px;
}
label {
  font-size: 20px;
}
</style>
