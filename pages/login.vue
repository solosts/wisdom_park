<template>
  <view class="pad-top-24 tc page-box">
    <view class="f-20 fw-bold">登录小微园区 体验智慧办公</view>
    <view class="f-14 mar-top-90">本机号码一键登录</view>
    <view class="phone-box fw-bold">177****0936</view>
    <view class="f-14 mar-top-12 f-12 color-5aa">其他号码登录</view>
    <view class="icon-box" @click="login">
      <uni-icons type="arrow-right" size="32" color="#fff"></uni-icons>
    </view>

    <view class="wx-login pad-lr-14 tc">
      <view class="dividing-box mar-bot-6">
        <view class="dividing-line"></view>
        <view class="dividing-text">使用微信登录</view>
        <view class="dividing-line"></view>
      </view>
      <uni-icons type="weixin" size="32" color="#626E8F"></uni-icons>
      <view class="mar-top-20 flex-center gap6">
        <uni-icons v-if="!isReader" type="circle" size="14" color="#CCCCC9" @click="changeReader"></uni-icons>
        <uni-icons v-if="isReader" type="circle-filled" size="14" color="#1684fc" @click="changeReader"></uni-icons>
        <view class="color-999 f-12">我已阅读并同意
          <span class="color-169">《服务协议》</span>和<span class="color-169">《隐私政策》</span>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup>
import { ref } from 'vue'

const isReader = ref(false)
const changeReader = () => {
  isReader.value = !isReader.value
}
const login = () => {
  if (!isReader.value) {
    return uni.showToast({
      title: '请先阅读协议！',
      icon: 'error',
      duration: 2000
    });
  }
  uni.showToast({
    title: '请先阅读协议！',
    duration: 2000,
    success: () => {
      uni.navigateTo({
        url: '/pages/tourist/index'
      })
    }
  });

}
</script>

<style lang="scss" scoped>
.page-box {
  position: relative;
  height: 100vh;
  background: linear-gradient(to bottom, #e4e9fc, #F1F5F8)
}

.phone-box {
  width: calc(100% - 76px);
  height: 44px;
  line-height: 44px;
  border-radius: 25px;
  margin: 20px auto 0;
  background-color: #fff;
}

.icon-box {
  width: 48px;
  height: 48px;
  line-height: 48px;
  border-radius: 50%;
  margin: 100px auto 0;
  background-color: #6377F5;
}

.wx-login {
  position: absolute;
  left: 0;
  bottom: 20px;
  width: 100%;
}

.dividing-box {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;

  .dividing-line {
    flex: 1;
    width: 100%;
    height: 1px;
    background-color: #CCCCC9;
  }

  .dividing-text {
    font-size: 14px;
    color: #273564 62%;
    padding: 0 14px;
  }
}
</style>