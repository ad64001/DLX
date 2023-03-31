<template>
	<view style="padding: 20rpx;">
		<view>
			<u-section title="友邻留言" lineColor="#00dee5" :right="false"></u-section>
		</view>
		<view>
			<uni-card style="border: 1rpx solid #ccc; border-radius: 30rpx; margin-top: 20rpx;" :isFull="true" v-for="(item,index) in 4">
				<view style="width: 100%; display: flex;">
					<view style="width: 10%;">
						<image style="margin: auto; display: flex; width: 50rpx; height: 50rpx;" src="../../../../static/icons/user_act.png" mode=""></image>
					</view>
					<view style="width: 65%; margin: auto; color: #666666;">
						友邻一号
					</view>
				</view>
				<u-line margin="10rpx"></u-line>
				<view style="width: 100%; height: 250rpx;" >
					<view style="width: 100%;">
						
						<view style="font-size: 35rpx; margin-top: 20rpx;display: flex;">你根本没在沈阳，你人呢</view>
						<view style="font-size: 35rpx; color: #666666; margin-top: 20rpx; margin-bottom: 20rpx;position: absolute; bottom: 20rpx;"><u-icon name="thumb-up"></u-icon>:1145141919</view>
						<view style=" margin-top: 20rpx; color: #666666;position: absolute; bottom: 10rpx;">发布时间:1919-4-16 10:24:36</view>
					</view>
				</view>
			</uni-card>
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
