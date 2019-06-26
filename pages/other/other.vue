<template>
	<view>
		<view>
			<button type="primary" plain="true" size="mini" @click="goIndex">返回首页</button>
			<button type="primary" plain="true" size="mini" @click="rediretTo">rediretTo首页</button>
		</view>
		<view>
			<button type="primary" plain="true" size="mini" @click="setTitle">设置标题</button>
		</view>
		<view>
			<button type="primary" plain="true" size="mini" @click="vibrateLong">手机振动</button>
		</view>
		<view>
			<button type="primary" plain="true" size="mini" open-type="share">分享</button>  
		</view>
		<view>
			<button type="primary" plain="true" size="mini" @click="rediretToMap">地图</button>
			<form @submit="openLocation">
				<button type="primary" plain="true" size="mini" formType="submit">在地图查看位置</button>
			</form>
		</view>
		<view>
			<button type="primary" plain="true" size="mini" @click="rediretToZYJ" >作业截</button>  
		</view>
			<view>
			<button type="primary" plain="true" size="mini" @click="zhiwen" >指纹识别</button>  
		</view>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				name:"other"
			}
		},
		methods: {
			//返回首页
			goIndex(){
				uni.switchTab({
						url: '/pages/index/index'
				});
			},
			//重定向首页
			rediretTo(){
				//navigateTo显示返回键
				//redirectTo 没有返回键
				uni.navigateTo({
						url: 'other-one/other-one?id=888888'
				});
			},
			//设置标题
			setTitle(){
				uni.setNavigationBarTitle({
						title: '多功能页'
				});
				uni.setNavigationBarColor({
						frontColor: '#ffffff',
						backgroundColor: '#1296db',
						animation: {
								duration: 400,
								timingFunc: 'easeIn'
						}
				})
			},
			//手机振动
			vibrateLong(){
				uni.vibrateLong({
						success: function () {
								console.log('振动 success');
						}
				});
			},
			//分享
			share(){
				uni.share({
						provider: 'weixin',
						type: 5,
						imageUrl: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/app/share-logo@3.png',
						title: '欢迎体验uniapp',
						miniProgram: {
								id: 'gh_abcdefg',
								path: 'pages/index/index',
								type: 0,
								webUrl: 'http://uniapp.dcloud.io'
						},
						success: ret => {
								console.log(JSON.stringify(ret));
						}
				});
			},
			//跳转地图页
			rediretToMap(){
				//navigateTo显示返回键
				uni.navigateTo({
						url: 'map/map'
				});
			},
			//分享
			onShareAppMessage(res) {
				if (res.from === 'button') {// 来自页面内分享按钮
					console.log(res.target)
				}
				return {
					title: '红莲天舞-test',
					desc:'我发现一个，不错的小程序，和我一起玩儿吧',
					path: '/pages/index/index',
					imageUrl:'../../static/img/wx-QRcode.jpg',
				}
			},
			//查看位置
			openLocation:function(e){
				uni.getLocation({
						type: 'gcj02', //返回可以用于uni.openLocation的经纬度
						success: function (res) {
								const latitude = res.latitude;
								const longitude = res.longitude;
								uni.openLocation({
										latitude: latitude,
										longitude: longitude,
										success: function () {
												console.log('success');
										}
								});
						}
				});
			},
			//小程序跳转到作业截
			rediretToZYJ(){
				uni.navigateToMiniProgram({
					appId: 'wx0548fcc6a08f6314',
					path: 'pages/index/index',
					success(res) {
						// 打开成功
						console.log(res)
					},
					fail(err){
						console.log(err)
					}
				})
			},
			//指纹识别
			zhiwen(){
				wx.startSoterAuthentication({
					 requestAuthModes: ['fingerPrint'],
					 challenge: '123456',
					 authContent: '请用指纹解锁',
					 success(res) {
						 console.log('指纹识别成功')
						 console.log(res)
					 },
					 fail(err){
						 console.log('识别失败')
						 console.log(err)
					 }
				})
			},
		}
	}
</script>

<style>

</style>
