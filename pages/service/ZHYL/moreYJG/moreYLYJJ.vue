<template>
		<view>
			<view style="padding: 20rpx;">
				<view>
					<u-swiper  height="350" effect3d></u-swiper>
				</view>
				<view style="margin-top: 20rpx; font-weight: bold; font-size: 45rpx; ">
					示例养老院
				</view>
				<view style="margin-top: 20rpx;">
					<u-section title="医院简介" lineColor="#22c786" :right="false"></u-section>
				</view>
				<uni-card style="border-radius: 20rpx; margin-top: 20rpx;" :isFull="true">
					<view><text v-for="ie in 34">示例养老院</text></view>
				</uni-card>
				
			</view>
			<view style="width: 100%; position: fixed; bottom: 0;">
				<button @click="toY" style="background: linear-gradient(90deg,#00d0f0,#00a0f0); color: #fff;">预约养老院</button>
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
			toY(){
				uni.navigateTo({
					url: 'moreLYY',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		}
	}
</script>

<style>

</style>
