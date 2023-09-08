<template>
	<view>
		<!-- 轮播图 -->
		<uni-swiper-dot :info="imgList" :current="dotCurrent" mode="round" :dotsStyles="dotsStyles">
			<swiper :current="current" autoplay :interval="3000" style="height: 228px;" @change="swiperChange">
				<swiper-item v-for="(item, index) in imgList" :key="index">
					<image class="wh-full" :src="item" mode="aspectFill"></image>
				</swiper-item>
			</swiper>
		</uni-swiper-dot>

		<!-- 内容部分 -->
		<view class="pad-14-10 mar-top--10 back-fff z-1 bor-rad-top-10">
			<!-- 园区介绍 -->
			<view class="flex-row-between gap8 color-fff">
				<view class="flex-col-star pad-left-16 back-5aa w-full flex-1 bor-rad-8 z-1 over-hidden h120">
					<view class="mar-top-16 f-16">园区介绍</view>
					<view class="mar-top-6 f-14">全方位服务体系</view>
					<view class="mar-top-12 mar-bot-22 f-12 w70 h26 line-h26 back-fff color-5aa tc bor-rad-25">去了解</view>
					<uni-icons custom-prefix="iconfont" class="bg-icon" type="icon-gongsi1" size="66" color="#fff"></uni-icons>
				</view>
				<view class="flex-1 flex-col-between">
					<view class="back-4bd bor-rad-8 color-2bc h54 pad-10-14 flex-row-between align-cen">
						<uni-icons custom-prefix="iconfont" type="icon-wendang" size="34" color="#fff"></uni-icons>
						<text class="flex-1 tc f-16">入园政策</text>
					</view>
					<view class="back-3ae bor-rad-8 color-17d h54 pad-10-14 flex-row-between align-cen">
						<uni-icons custom-prefix="iconfont" type="icon-fuwu" size="34" color="#fff"></uni-icons>
						<text class="flex-1 tc f-16">园区服务</text>
					</view>
				</view>
			</view>

			<!-- 园区办事指南 -->
			<view class="mar-top-18 bor-rad-8 pad-14-10 guide-box">
				<!-- 头部 -->
				<view class="flex-row-between algin-cen">
					<view class="flex-1 flex-row-start gap8">
						<uni-icons class="bor-rad-25 back-ff7 flex-center wh40" custom-prefix="iconfont" type="icon-a-zu51" size="26"
							color="#fff"></uni-icons>
						<view class="flex-col-center gap2">
							<text class="f-14 fw-bold color-333">园区办事指南</text>
							<text class="f-12 color-999">有问题，找我行</text>
						</view>
					</view>
					<view class=" flex-row-end gap4 line-h40">
						<uni-icons type="info" size="16" color="#faa24b"></uni-icons>
						<text class="f-12 color-999">左右滑动可查看更多</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script setup>
import { ref } from 'vue';

const dotsStyles = {
	bottom: 20,
	backgroundColor: '#cdd4d1',
	border: '#cdd4d1',
	selectedBackgroundColor: '#fff',
	selectedBorder: '#fff',
}
const imgList = ['../../static/images/1.jpg', '../../static/images/2.jpg', '../../static/images/3.jpg']
const current = ref(0);
const dotCurrent = ref(0);
const swiperChange = (e) => {
	dotCurrent.value = e.detail.current;
}
</script>

<style lang="scss" scoped>
.bg-icon {
	position: absolute;
	right: 0;
	bottom: -12px;
}

.pad-10-14 {
	padding: 10px 14px;
}

.pad-14-10 {
	padding: 14px 10px;
}

.guide-box {
	box-shadow: 0px 5px 15px 0px rgba(0, 0, 0, 0.07);
}
</style>
