<template>
  <view class="index">
    <nut-circle-progress
      :progress="progress"
      path-color="#3c7bf140"
      color="#3c7bf1"
      stroke-linecap="square"
      stroke-width="10"
      radius="20"
    >
      {{ progress }}
    </nut-circle-progress>
    <nut-button @click="onTap">开始</nut-button>
  </view>
</template>

<script setup>
import { ref } from "vue";
let timer = null;
const progress = ref(0);

const onTap = () => {
  if (timer) {
    clearTimeout(timer);
    timer = null;
  } else {
    updateProgress();
  }
};

const updateProgress = () => {
  timer = setTimeout(() => {
    if (progress.value < 100) {
      progress.value++;
      updateProgress();
    }
  }, 1000);
};
</script>

<style lang="scss">
.index {
  margin-top: 100rpx;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
