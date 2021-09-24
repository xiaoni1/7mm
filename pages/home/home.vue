<template>
	<view class="home">
	<!-- #ifdef H5 --><!-- h5页面显示 -->
	<Header/>
	<view class="area flex_box jca">
		<view class="content" style="display: none;">
			<view class="f26px tc">短链接生成</view>
			<view class="flex_box inputbox aic jsb">
				<input type="text" value="text" class="input" v-model="input_text" placeholder="粘贴长网址并缩短它" />
				<view class="main-bg btn f12px white tc">缩短</view>
			</view>
			<view class="f12px tc">使用我们的服务，接受<text class="main-color pl10rpx pr10rpx" @click="switchPage">服务条款</text>和<text class="main-color pl10rpx pr10rpx" @click="switchPage"> 隐私政策 </text></view>
		   <!-- 列表 -->
			<view class="list white-bg" v-for="(item,index) in list" :key="index">
				<view class="topBox p30rpx flex_box jsb aic">
					<view class="left">
						<view class="f14px gray5">{{ item.title }}</view>
						<view class="f14px mt15rpx gray5">{{ item.changeTitle }}</view>
					</view>	
					<view class="right f14px p15rpx gray5 pr showTip">
						<text>{{ item.time }}</text>
						<view v-if="show" class="pa" style="background-color: #333333;color: #fff;bottom: 120% ;let:10%;padding: 15rpx;border-radius: 10rpx;">生成日期</view>
					</view>	
					
				</view>
				<view class="bottomBox p30rpx flex_box jsb aic">
					<view class="left ">
						<view class="f14px  gray5">
							<text class="origintitle">{{ item.origntitle }}</text>
							<text class="white bg f12px" @click="copy(item.origntitle)">复制</text>
						</view>
						<view class="mt15rpx">
							<image src="https://axure-file.lanhuapp.com/4736b466-e846-4efc-a46d-c93dc367191b__2d1f06278915b03dcce27cfaed6f650e.svg" mode=""></image>
							<text class="f14px main-color ml10rpx ">注册使用查看详细统计数据</text>
						</view>
					</view>	
					<view class="right f12px p20rpx gray5">
						<image class="mr15rpx" src="https://axure-file.lanhuapp.com/4736b466-e846-4efc-a46d-c93dc367191b__24cad16c85a523d09bc0066525ffe6d9.svg" mode=""></image>
					    点击<text class="white main-bg f15px number">{{ item.num }}</text>次
					</view>				  
				</view>
			</view>
		
		</view>
		<view class="content_login mt30rpx">
			<view class="box1 flex_box jsb">
				<view class="box white-bg" v-for="item in login_itemList" >
					<view class="f12px">{{ item.title }}</view>
					<view class="mt40rpx flex_box jsb">
						<text class="f15px">{{ item.num }}</text>
						<image :src="item.icon" mode=""></image>
					</view>
				</view>
			</view>
		</view>
	</view>	
	
		
	<!-- #endif -->
		<!-- 小程序显示 -->
		<!-- #ifdef MP-WEIXIN -->   
		
		<!-- #endif -->
		<view class="bottom" v-if="bottomShow">
			<Bottom/>
		</view>
		
	</view>
</template>

<script>
	import Header from '../components/header.vue'
	import Bottom from '../components/bottom.vue'
	export default {
		components: {
			Header,Bottom	
		},
		data() {
			return {
				input_text: '',
				show: false,
				bottomShow: true,
				list: [],
				login_itemList: [
					{
						title: '所有网址',
						num: 1,
						icon: 'https://axure-file.lanhuapp.com/4736b466-e846-4efc-a46d-c93dc367191b__a041e39e72a88bba56d7e2fb2cd8b3d3.svg'
					},
					{
						title: '总点击次数',
						num: 1,
						icon: 'https://axure-file.lanhuapp.com/4736b466-e846-4efc-a46d-c93dc367191b__a041e39e72a88bba56d7e2fb2cd8b3d3.svg'
					},
					{
						title: '本月新添加链接',
						num: 1,
						icon: 'https://axure-file.lanhuapp.com/4736b466-e846-4efc-a46d-c93dc367191b__1561865819e035342a63611aef0980d5.svg'
					},
					{
						title: '2021年九月的链接数量',
						num: 1,
						icon: 'https://axure-file.lanhuapp.com/4736b466-e846-4efc-a46d-c93dc367191b__0edf2786751ced84688f7805babeff00.svg'
					}
				]
			}
		},
		watch: {
		  	
		},
		onLoad() {
			this.getList()
		},
		methods: {
			getList() {
				this.list =  [
					{
					  "title": 'www.souxiu.cn',
					  "origntitle": 'https://www.souxiu.cn',
					  "time": '2021-09-16',
					  "changeTitle": 'https://123.com/dfasW31',
					  'num': 3
					}
				
				]
				if(this.list.length!=0){
					this.bottomShow = false
					
				}
				
			},
			switchPage() {
				uni.navigateTo({
					url: '../termsOfServince/index'
				})
			},
			copy(text) {
				alert(text)
				uni.setClipboardData({
					data: text,
					fail() {
					  alert('请手动复制')	
					}
					
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.home {
		background-color: rgb(242, 242, 242);
		height: 100%;
	
		.area {
			min-height: 90.1%;
			width: 100%;
			background-color: rgb(242, 242, 242);
		}
		@media screen and(max-width: 768px){
			.content {
				width: 100%!important;
			}
			.btn {
				width: 20%!important;
			}
		}
		.content {
			width: 50%;
			margin-top: 100rpx;
			.inputbox {
				margin: 70rpx 0 40rpx 0;
				justify-content: center;
				.input {
					width: 100%;
					border: 1px solid #DCDCDC; 
					border-radius: 5rpx 0 0 5rpx;
					padding-left: 20rpx;
					height: 72rpx;
					background: #FFFFFF;
				}
				@media screen  and(max-width:1200px){
					.btn {
						width: 20%!important;
					}
				}
				.btn {
					width: 10%;
					padding: 20rpx 35rpx;
					border-radius: 0 5rpx 5rpx 0;
				}
			}
			.list {
				margin: 50rpx 0;
				border-radius: 10rpx;
				.topBox {
					border-bottom: 1px solid #dcdcdc;
					.right {
						border: 1px solid rgb(220,227,233);
						border-radius: 10rpx;
					}
				}
				.bottomBox {
					image {
						width: 30rpx;
						height: 30rpx;
					}
					.left {
						.origintitle{
							color:rgb(245, 154, 35);
						}
						.bg {
							background-color: rgb(245, 154, 35);
							padding: 5rpx;
							border-radius: 3rpx;
							margin-left: 10rpx;
						}
					}
					.right {
						border-radius: 10rpx;
						border: 1px solid rgb(220,227,233);
						.number {
							padding: 5rpx 10rpx;
							border-radius: 5rpx;
							margin: 0 5rpx;
						}
					}
				}
			}
		}
		.content_login {
			width: 50%;
			.box1 {
				image {
					width: 50rpx;
					height: 50rpx;
				}
				.box {
				   width: 23%;
				   padding: 30rpx;
				}
			}
		}
	}
	
</style>
