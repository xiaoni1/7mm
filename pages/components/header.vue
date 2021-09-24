<template>
	<view class="top main-bg white flex_box jsb p25rpx">
		<view class="flex_box aic">
			<text class="f15px">7mm.cn</text>
			<view class="homePage">
				<image src="https://axure-file.lanhuapp.com/4736b466-e846-4efc-a46d-c93dc367191b__6d7b9857062260300f01d1e957e0792b.svg" mode=""></image>
				<text class="f15px ml30rpx opa">首页</text>
			</view>
		</view>
		<view class=" flex_box mr30rpx">
			<image class="mr30rpx" src="https://axure-file.lanhuapp.com/4736b466-e846-4efc-a46d-c93dc367191b__6fa1c45e5ab20382a42e050e3cb494f4.svg" mode=""></image>
			<view class="opa" style="display: none;">
				<text class="f15px">登录</text><text class="ml10rpx mr10rpx">/</text><text class="f15px">注册</text>
			</view>
			<view class="loginInfo flex_box aic pr">
				<image src="../../static/logo.png" class="headimg" mode=""></image>
				<view class="ml20rpx">
					<text class="f14px">kdskdkd</text>
					<text class="iconfont icon-xiala" @click="settingList"></text>
				</view>
				<view class="setting pa white-bg" v-if="show">
					<view class="list p20rpx">
						<image src="https://axure-file.lanhuapp.com/4736b466-e846-4efc-a46d-c93dc367191b__28f83bfde619b5c297639acbd8192c29.svg" mode=""></image>
						<text class="f12px black ml10rpx">账户设置</text>
					</view>
					<view class="list p20rpx">
						<image src="https://axure-file.lanhuapp.com/4736b466-e846-4efc-a46d-c93dc367191b__46739696eeef1dc29abe512c97dd8e04.svg" mode=""></image>
						<text class="f12px black ml10rpx">安全退出</text>
					</view>
					
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				show: false
			}
		},
		methods: {
			settingList() {
				this.show = true
			}
		}
	}
</script>

<style scoped lang="scss">
	.top {
		image {
			width: 35rpx;
			height: 35rpx;
		}
		.homePage {
			margin-left: 50rpx;
		}
		.opa {
			color: rgba(255,255,255,.8);
		}
		.loginInfo {
			.headimg {
				border-radius: 50%;
				width: 40rpx;
				height: 40rpx;
			}
			.setting {
				border-radius: 10rpx;
				top: 70rpx;
				right: 0;
				image {
					width: 30rpx;
					height: 30rpx;
				}
				.list {
					&:hover {
						background-color: rgba(0,0,0,.1);
					}
				}
			}
		}
	}
</style>
