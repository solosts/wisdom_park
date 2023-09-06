<template>
	<view class="content">
		<button @click="toLogin">去登录</button>
	</view>
</template>

<script setup>
const toLogin = () => {
	uni.navigateTo({
		url: '/pages/login'
	})
}
</script>

<style lang="scss" scoped></style>
