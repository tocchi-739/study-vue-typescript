<script setup lang="ts">
import { ref, defineEmits } from "vue";

const inputtingDescription = ref<string>("");

const emit = defineEmits(["post-tweet"]);
const postTweet = () => {
  emit("post-tweet", inputtingDescription.value);
  inputtingDescription.value = "";
};
</script>

<template>
  <div class="form-container">
    <input v-model="inputtingDescription" />
    <button class="save-button" @click="postTweet()">post</button>
  </div>
</template>

<style scoped>
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

.save-button {
  padding: 5px 20px;
  margin-top: 10px;
  background-color: #1db7af;
  color: white;
}
</style>
