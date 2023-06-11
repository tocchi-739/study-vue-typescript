<script setup lang="ts">
import { ref } from "vue";

const tweets = ref([
  { id: 0, description: "Hello World" },
  { id: 1, description: "foobar" },
]);

const inputtingDescription = ref<string>("");

const postTweet = () => {
  const tweet = { id: Math.random(), description: inputtingDescription.value };
  tweets.value.push(tweet);
  inputtingDescription.value = "";
};

const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter((t) => t.id !== id);
};
</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
    <div class="form-container">
      <input v-model="inputtingDescription" />
      <button class="save-button" @click="postTweet()">post</button>
    </div>
    <div class="tweet-container">
      <p v-if="tweets.length <= 0">No tweets have been added.</p>
      <ul>
        <li v-for="tweet in tweets" v-bind:key="tweet.id" class="tweet-list">
          <span>{{ tweet.description }}</span>
          <button class="delete-button" @click="deleteTweet(tweet.id)">
            delete
          </button>
        </li>
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

.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: aliceblue;
  padding: 24px 0;
  width: 60%;
  margin-bottom: 12px;
  border-radius: 4px;
}

ul {
  padding: 0;
}
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
.save-button {
  padding: 5px 20px;
  margin-top: 10px;
  background-color: #1db7af;
  color: white;
}
.delete-button {
  padding: 5px 20px;
  background-color: #b71d1d;
  color: white;
}
</style>
