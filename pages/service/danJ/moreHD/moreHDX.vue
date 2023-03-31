<template>
	<view style="padding: 20rpx;">
		<view>
			<view>
				<u-swiper :list="list"></u-swiper>
			</view>
		</view>
		<view>
			<uni-card :isFull="true" style="margin-top: 20rpx; border-radius: 30rpx;" >
				<view style="font-weight: bold; font-size: 45rpx; " >活动示例</view>
				<view>
					<view style="margin-top: 20rpx;">
						<u-section title="活动详情" lineColor="#F62D59" :right="false"></u-section>
					</view>
					<view style="margin-top: 10rpx; text-indent: 2em; color: gray; word-break: break-all;">
						示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例
						示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例
						示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示
						例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例
					</view>
				</view>
			</uni-card>
			<button @click="tl" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#F62D59,#FF2D69); color: #fff; margin: 30rpx auto;">报名</button>
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
			tl(){
				this.et('报名成功')
			}
		}
	}
</script>

<style>

</style>
