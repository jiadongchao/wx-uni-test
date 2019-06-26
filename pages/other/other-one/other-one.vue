<template>
	<view>
		id = {{id}}
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:""
			}
		},
		onLoad(option) {
			this.id = option.id;
    },
		methods: {
			
		}
	}
</script>

<style>

</style>
