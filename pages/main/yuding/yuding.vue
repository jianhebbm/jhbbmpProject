<template>
	<view style="background-color: yellow;margin: 10px;">
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		mounted() {
			uni.showToast({
				icon:'loading',
				title:'请稍后……',
				duration:500
			})
			console.log('已跳转到预订页面')
		}
	}
</script>

<style lang="scss">

</style>
