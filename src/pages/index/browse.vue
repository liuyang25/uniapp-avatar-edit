<template>
  <view class="content">
    <swiper class="swiper" previous-margin="80px" next-margin="80px"
      @change="onChange" 
    >
      <!--swiper-item class="testStyle_out">
        <view class="swiper-item testStyle_in" :style="testStyle">6</view>
      </swiper-item-->
      <swiper-item v-for="item in templates" :key="item.name">
        <view class="swiper-item_out" :style="[item.outerStyle]">
          <view class="swiper-item_in" :style="[item.innerStyle]">{{item.content}}</view>
        </view>
        <view class="item-name">{{item.name}}</view>
      </swiper-item>
    </swiper>
    <view class="menus">
      <button plain="false" @click="onEdit">编辑</button>
      <button plain="false" @click="onCopy">复制</button>
      <button v-if="this.mode==2" plain="false" @click="onDelete">删除</button>
    </view>
  </view>
</template>

<script>
import Vue from 'vue'
import templates from '../../config/templates'

export default {
  data() {
    return {
      mode: 0,
      templates: [],
      currentItem: 0,
    }
  },
  onLoad(option) {
    console.log(option)
    this.mode = option.mode
    if (this.mode == 2) {
      uni.getStorage({
        key: 'savedData',
        success: function(res) {
          this.templates = res.data
        },
        fail: function(res) {
          this.templates = []
        }
      })
    } else {
      this.templates = templates
    }
  },
  methods: {
    onChange(event) {
      // event.detail = {current: current, source: source}
      this.currentItem = event.detail.current
      console.log(this.currentItem)
    },
    onEdit() {
      uni.navigateTo({
        url: `/pages/index/edit?mode=${this.mode}&index=${this.currentItem}`
      })
    },
    onCopy() {
      uni.navigateTo({
        url: `/pages/index/edit?mode=${this.mode}&index=${this.currentItem}&copy=true`
      })
    },
    onDelete() {
      this.templates.splice(this.currentItem, 1)
      uni.setStorage({
        key: 'savedData',
        data: this.templates,
        success: function() {
          uni.showToast({
            title: '删除成功',
            duration: 2000
          });
        },
        failed: function() {
          uni.showToast({
            title: '删除失败',
            duration: 2000
          });
        }
      })
    } 
  }
}
</script>

<style>
.content {
  text-align: center;
}
.swiper {
  width: 100%;
  height: 500upx;
}
swiper-item {
  box-sizing: border-box;
  padding: 20upx;
  background-color: white;
}
.swiper-item_out {
}
.swiper-item_in {
  border: 1px solid red;
  margin: 20upx;
  margin-top: 50upx;
  height: 300upx;
  line-height: 300upx;
}
.testStyle_in{
  background-color: black;
  color: white;
  text-shadow: 0 0 1upx, 0 0 3upx;
  border-radius: 100%;
  font-size: 200upx;
  border: solid 20upx white;
}
.testStyle_out {
  background-color: black;
}
.menus {
}
.item-name {
  color: black;
  background-color: white;
}
</style>
