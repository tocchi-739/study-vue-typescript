<script setup lang="ts">
import { ref } from "vue";
import TweetPost from "./TweetPost.vue";
import TweetList from "./TweetList.vue";

const tweets = ref([
  { id: 0, description: "Hello World" },
  { id: 1, description: "foobar" },
]);

const postTweet = (description: string) => {
  const tweet = { id: Math.random(), description: description };
  tweets.value.push(tweet);
};

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter((t) => t.id !== id);
};
</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
    <TweetPost @post-tweet="postTweet" />
    <div class="tweet-container">
      <p v-if="tweets.length <= 0">No tweets have been added.</p>
      <ul>
        <TweetList :tweets="tweets" @delete-tweet="deleteTweet" />
      </ul>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100vw;
}

ul {
  padding: 0;
}
</style>
