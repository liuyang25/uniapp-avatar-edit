<template>
  <view class="content">
    <swiper class="swiper" previous-margin="80px" next-margin="80px">
      <swiper-item>
        <view class="swiper-item" :class="typeClass">A</view>
      </swiper-item>
      <swiper-item>
        <view class="swiper-item">B</view>
      </swiper-item>
      <swiper-item>
        <view class="swiper-item">C</view>
      </swiper-item>
      <swiper-item>
        <view class="swiper-item">D</view>
      </swiper-item>
      <swiper-item>
        <view class="swiper-item">E</view>
      </swiper-item>
    </swiper>
    <view class="menus">
      <button plain="false">编辑</button>
      <button plain="false">复制</button>
      <button plain="false">删除</button>
    </view>
  </view>
</template>

<script lang="ts">
import Vue from 'vue'
export default {
  data() {
    return {
    }
  },
  onLoad() {},
  methods: {}
}
</script>

<style>
.content {
  text-align: center;
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
