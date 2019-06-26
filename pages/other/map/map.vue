<template>
	<view>
		<view class="page-section page-section-gap">
			<map style="width: 100%; height: 300px;" 
			:latitude="latitude" 
			:longitude="longitude" 
			:markers="covers">
			</map>
		</view>
		<view class="page-body">
			<view class="btn-area">
				<navigator url="../navigate/navigate?title=navigate" hover-class="navigator-hover">
						<button type="default">跳转到新页面</button>
				</navigator>
				<navigator url="redirect/redirect?title=redirect" redirect hover-class="other-navigator-hover">
						<button type="default">在当前页打开</button>
				</navigator>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
						title: 'map',
            latitude: 39.909,
            longitude: 116.39742,
            covers: [{
                latitude: 39.909,
                longitude: 116.39742,
                iconPath: '../../../static/img/location.png'
            }, {
                latitude: 39.90,
                longitude: 116.39,
                iconPath: '../../../static/img/location.png'
            }]
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
