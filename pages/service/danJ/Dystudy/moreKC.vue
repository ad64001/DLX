<template>
	<view style="padding: 20rpx;">
		<uni-grid :column="2" :showBorder="false" :highlight="false">
			<uni-grid-item>
				<view style="width: 90%;height: 400rpx; box-shadow:0rpx 0rpx 20rpx #eee; border-radius: 40rpx; margin: auto;">
					<navigator style="width: 100%;height: 400rpx;border-radius: 40rpx;">
					<view>
						<image style="width: 100%; height: 250rpx;border-radius: 40rpx;" src="../../../../static/image/banner2.jpg" mode=""></image>
					</view>
					<view style="padding: 5rpx; word-break: break-all; font-weight: bold;">
						中国党员示例示例示例示例例示例中国党员...
					</view>
					<view style="position: absolute; right: 45rpx; border: 1rpx solid orangered; color: orangered;width: 100rpx; text-align: center;">已完成</view>
					</navigator>
				</view>
			</uni-grid-item>
			<uni-grid-item>
				<view style="width: 90%;height: 400rpx; box-shadow:0rpx 0rpx 20rpx #eee; border-radius: 40rpx; margin: auto;">
					<navigator style="width: 100%;height: 400rpx;border-radius: 40rpx;">
					<view>
						<image style="width: 100%; height: 250rpx;border-radius: 40rpx;" src="../../../../static/image/banner2.jpg" mode=""></image>
					</view>
					<view style="padding: 5rpx; word-break: break-all; font-weight: bold;">
						中国党员示例示例示例示例例示例中国党员...
					</view>
					<view style="position: absolute; right: 45rpx; border: 1rpx solid #22c876; color: #22c876;width: 100rpx; text-align: center;">未完成</view>
					</navigator>
				</view>
			</uni-grid-item>
		</uni-grid>
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
