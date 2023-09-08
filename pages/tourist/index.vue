<template>
	<view>
		<!-- 轮播图 -->
		<uni-swiper-dot :info="imgList" :current="dotCurrent" mode="round" :dotsStyles="dotsStyles">
			<swiper :current="current" circular autoplay :interval="3000" style="height: 228px;" @change="swiperChange">
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
			<view class="mar-top-18 bor-rad-8 pad-14-10 card-box">
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
				<!-- 滑动图 -->
				<swiper :current="guideCurrent" circular class="mar-top-14" style="height: 120px;">
					<swiper-item v-for="(item, index) in 3" :key="index">
						<view class="pad-10 pad-top-12 back-ff8 wh-full z-1">
							<text class="title-tag">企业入驻{{ index + 1 }}</text>
							<view class="mar-top-16 f-16 fw-bold">企业入驻园区有那些优势？</view>
							<view class="mar-top-18 f-14 color-999">点击查看</view>
							<uni-icons class="right-icon" custom-prefix="iconfont" type="icon-a-zu51" size="76"
								color="#fff"></uni-icons>
						</view>
					</swiper-item>
				</swiper>
			</view>

			<!-- 热门场地 -->
			<view class="mar-top-12 bor-rad-8 pad-14-10 card-box">
				<view class="flex-row-between algin-cen">
					<text class="f-20 fw-bold color-333">热门场地
						<text class="color-999 f-12 fw-200">（可预约）</text>
					</text>
					<view class="f-12 color-999 flex-center">
						<text>查看全部</text>
						<uni-icons type="forward" size="14" color="#999"></uni-icons>
					</view>
				</view>
				<!-- 场地列表 -->
				<view class="mar-top-10 flex-row-start gap12">
					<view class="site-item" v-for="item in 3">
						<image src="../../static/images/4.jpg" mode="aspectFill"></image>
						<view class="tc f-12 mar-tb-6 color-ff7"><text class="f-16">4</text>元/m²·日</view>
						<text class="site-tag f-12">办公室</text>
					</view>
				</view>
				<!-- 导航 -->
				<view class="flex-row-start gap8 mar-top-32">
					<uni-icons class="bor-rad-25 back-5aa flex-center wh40" custom-prefix="iconfont" type="icon-daohang" size="26"
						color="#fff"></uni-icons>
					<view class="flex-col-center gap2">
						<text class="f-14 fw-bold color-333">园区导航</text>
						<text class="f-12 color-999">一键轻松导航</text>
					</view>
				</view>
				<!-- 地图 -->
				<view class="map-box mar-top-10">
					<map :scale="14" :longitude="115.86459" :latitude="28.68946" :markers="covers"></map>
					<view class="map-tag flex-row-between algin-cen">
						<text class="f-16 color-333 mar-left-14 mar-top-4">武汉科技城</text>
						<view class="flex-row-end algin-cen gap20">
							<uni-icons type="paperplane-filled" size="24" color="#5c5b58"></uni-icons>
							<uni-icons type="phone-filled" size="24" color="#5c5b58"></uni-icons>
						</view>
					</view>
				</view>
			</view>

			<!-- 精选企业 -->
			<view class="mar-top-12 bor-rad-8 pad-14-10 card-box">
				<text class="fw-bold f-20">精选企业</text>
				<view class="enterprises-list mar-top-14">
					<swiper :current="enterprisesCurrent" circular :display-multiple-items="2"
						style="width: calc(100% + 56px);height: 128px;">
						<swiper-item v-for="(item, index) in 3" :key="index">
							<view class="wh-full pad-right-12">
								<view class="wh-full z-1">
									<image class="wh-full" src="../../static/images/4.jpg" mode="aspectFill"></image>
									<text class="site-tag">智能</text>
									<view class="map-tag">浙江蓓斯智能科技有限公司</view>
								</view>
							</view>
						</swiper-item>
					</swiper>
				</view>
			</view>

			<!-- 园区咨讯 -->
			<view class="mar-top-12 bor-rad-8 pad-14-10 card-box">
				<text class="fw-bold f-20">园区咨讯</text>
				<!-- 带图片展示 -->
				<view class="mar-top-8 flex-row-between gap8 pad-bot-14">
					<view>
						<view class="fw-bold f-16 row-2">中建设计集团、中建一局集团来科技城洽谈合作</view>
						<view class="mar-top-4 f-12 row-2 color-666">9月29日下午，中国中建设计集团有限公司上海分公司副总苏粤、中国建设计集团有限公司上海分公司</view>
					</view>
					<image class="h90 w130 flex-none" src="../../static/images/4.jpg" mode="aspectFill"></image>
				</view>
				<Dividing />
				<!-- 列表展示 -->
				<view class="pad-top-14">
					<view class="mar-bot-8">
						<text class="title-tag">实时资讯</text>
					</view>
					<view class="line-h22">
						<view class="row-1">县人大常委会组织人大代表到科技城开展视察活动</view>
						<view class="row-1">全县建筑业企业座谈会在科技城召开</view>
						<view class="row-1">县人大常委会组织人大代表到科技城开展视察活动</view>
						<view class="row-1">县人大常委会组织人大代表到科技城开展视察活动</view>
						<view class="row-1">县人大常委会组织人大代表到科技城开展视察活动</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script setup>
import { ref } from 'vue';
import Dividing from '../../components/Dividing.vue';

// 顶部轮播图
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

// 办事指南
const guideCurrent = ref(0);

// 导航
const covers = [{
	id: 1,
	longitude: 115.86463,
	latitude: 28.68850,
	width: 14,
	height: 20,
}]

// 精选企业
const enterprisesCurrent = ref(0);
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

.card-box {
	box-shadow: 0px 5px 15px 0px rgba(0, 0, 0, 0.07);
}

// 办事指南
.title-tag {
	width: 62px;
	height: 20px;
	padding: 1px 4px;
	border-radius: 2px;
	line-height: 1;
	color: #fff;
	background-color: #FF7F00;
}

.right-icon {
	position: absolute;
	right: 0;
	bottom: -4px;
}

// 热门场地
.site-item {
	position: relative;
	width: calc((100% - 24px) / 3);
	border-radius: 4px;
	box-shadow: 0px 2px 6px 0px rgba(0, 0, 0, 0.34);
	overflow: hidden;

	image {
		display: block;
		width: 100%;
		height: 90px;
	}
}

.site-tag {
	position: absolute;
	top: 0;
	left: 0;
	padding: 2px 4px;
	color: #fff;
	background-color: rgba(#000, 0.3);
}

// 导航
.map-box {
	position: relative;
	height: 88px;
	box-shadow: 0px 2px 6px 0px rgba(0, 0, 0, 0.34);
	overflow: hidden;

	map {
		width: 100%;
		height: 110px;
	}
}

.map-tag {
	position: absolute;
	bottom: 0;
	left: 0;
	width: 100%;
	// height: 26px;
	background-color: rgba(#000, 0.13);
}

// 企业
.enterprises-list {
	width: 100%;
	height: 128px;
	overflow: hidden;

	.site-tag {
		background-color: #9e6f5b;
	}

	.map-tag {
		color: #fff;
		padding: 4px 4px;
	}
}
</style>
