<template>
	<view>
		<view style="margin-top: 10rpx; padding: 20rpx;">
			<view>
				<u-section title="停车位" lineColor="#00dee5" :right="false"></u-section>
			</view>
			<view style="margin-top: 30rpx;">
				<uni-card style="margin-top: 20rpx; border: 1rpx solid #ccc; border-radius: 20rpx; " :isFull="true" v-for="(item,index) in 4">
					<view style="font-size: 35rpx; font-weight: bold; color: #333333;">221号停车位</view>
					<u-line margin="10rpx"></u-line>
					<view style="width: 100%; display: flex;">
						<view style="width: 40%;">
							<image style="width: 300rpx;height: 200rpx; background: #eee;" src="" mode="scaleToFill"></image>
						</view>
						<view style="width: 60%; margin-left: 60rpx; font-size: 35rpx;">
							<text v-for="it in 19">示例</text>
						</view>
					</view>
				</uni-card>
			</view>
			
			
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
