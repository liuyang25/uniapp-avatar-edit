<template>
  <view class="content">
    <button class="btn" @click="handleNew">新建</button>
    <button class="btn" @click="handleView">浏览</button>
  </view>
</template>

<script lang="ts">

export default {
  data() {
    return {}
  },
  onLoad() {},
  methods: {
    handleNew() {
      uni.navigateTo({
        url: '/pages/index/browse?mode=1'
      })
    },
    handleView() {
      uni.navigateTo({
        url: '/pages/index/browse?mode=2'
      })
    }
  }
}
</script>

<style>
.content {
  text-align: center;
  position: relative;
  height: 100vh;
}
.content .btn {
  height: 40%;
  width: 100%;
  padding: 20upx;
  margin-bottom: 20upx;
  display: flex;
  justify-content: center;
  align-items: center;
}
.swiper {
  width: 100%;
  height: 400upx;
}
.swiper-item {
  border: 1px solid red;
  margin: 20upx;
  margin-top: 50upx;
  height: 300upx;
  line-height: 300upx;
}
</style>
