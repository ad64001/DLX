<template>
	<view style="padding: 20rpx;">
		<view>
			<uni-group style="padding: 10rpx;" margin-top="20" mode="card" v-for="(item,index) in 4">
				<view>
					<view style="font-weight: bold; font-size: 35rpx; margin-bottom: 10rpx;">车牌号:114514</view>
					<u-line></u-line>
					<view style="margin-top: 20rpx;">车架号：114514</view>
					<view style="margin-top: 20rpx;">车辆类型：大型车</view>
					<view style="margin-top: 20rpx;">公里数：114514/km</view>
					<view style="margin-top: 20rpx;">电话号码：11451419192</view>
				</view>
			</uni-group>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
