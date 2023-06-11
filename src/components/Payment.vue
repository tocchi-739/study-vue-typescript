<script setup lang="ts">
import { reactive, computed } from "vue";

const item1 = reactive({ name: "Desk", price: 300 });
const item2 = { name: "Bike", price: 500 };

const url = "https://www.yahoo.co.jp";

const buy = (itemName: string) => {
  alert(itemName + "を購入しますか？");
};

const clear = () => {
  item1.name = "";
  item1.price = 0;
};

const budget = 50000;

const priceLabel = computed(() => {
  if (item1.price > budget) {
    return "予算オーバー";
  } else {
    return item1.price + "円";
  }
});
</script>

<template>
  <div class="container">
    <h1>Payment</h1>
    <input v-model="item1.name" />
    <input v-model="item1.price" />
    <button v-on:click="clear">clear</button>
    <div class="payment">
      <label>{{ item1.name }}</label>
      <label>{{ priceLabel }}</label>
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
