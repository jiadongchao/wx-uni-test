<template>
	<view class="content">
		<!-- <image class="logo" src="/static/img/logo.png"></image> -->
		<view class="logo">
			<open-data type="userAvatarUrl"></open-data>
		</view>
		<view>
<!-- 		 <button type="primary" plain="true" size="mini">获取头像</button> -->
			<text class="title">手机品牌:{{brand}}</text>
		</view>
		<view>
			<text class="title">用户昵称:</text>
			<open-data type="userNickName"></open-data>
		</view>
				<view>
			<text class="title">所在城市:</text>
			<open-data type="userCity"></open-data>
		</view>
	</view>
</template>

<script>
	import $api from '../../static/const/api.js'
	export default {
		data() {
			return {
				brand:'品牌',
			}
		},
		onLoad() {
			this.getBrand()
		},
		methods: {
			//获取手机品牌
			getBrand(){
				uni.getSystemInfo({
					success: (res=>{
						this.brand = res.brand
					}),
					fail:(err=>{
						console.log(err)
					})
				});
			},
		},
	}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
	}

	.logo {
		height: 200upx;
		width: 200upx;
		margin-top: 200upx;
		display: inline-block;
		border-radius: 50%;
		overflow: hidden;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
</style>
