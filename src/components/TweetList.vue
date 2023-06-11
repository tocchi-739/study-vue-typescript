<script setup lang="ts">
import { defineProps, defineEmits } from "vue";

type Tweet = {
  id: number;
  description: string;
};

type Props = {
  tweets: Tweet[];
};

const emit = defineEmits(["delete-tweet"]);
const deleteTweet = (id: number) => {
  emit("delete-tweet", id);
};

defineProps<Props>();
</script>

<template>
  <li v-for="tweet in tweets" v-bind:key="tweet.id" class="tweet-list">
    <span>{{ tweet.description }}</span>
    <button class="delete-button" @click="deleteTweet(tweet.id)">delete</button>
  </li>
</template>

<style scoped>
.tweet-list {
  list-style: none;
  background-color: #b2d1e8;
  width: 300px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 10px;
  padding: 8px 20px;
}
</style>
