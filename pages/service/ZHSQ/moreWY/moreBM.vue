<template>
	<view style="padding: 20rpx;">
		<view>
			<u-section title="服务列表" lineColor="#00dee5" :right="false"></u-section>
		</view>
		<view style="margin-top: 20rpx;">
			<uni-list>
				<uni-list-item v-for="item in 4" to="moreTZNR/moreTZNR">
					<view slot="header">
						<image style="border-radius: 20rpx; width: 200rpx; height: 200rpx;" src="../../../../static/hb/zhixiang.png" mode=""></image>
					</view>
					<view slot="body" style="margin-left: 20rpx; margin-top: 20rpx;">
						<view style="font-weight: bold;font-size: 35rpx;">楼道打扫服务</view>
						<view style="font-weight: bold;">示例动态</view>
						<view>示例动态示例动态示例动态示例动态示例动态示例动态示例动态示例动态示例动态</view>
					</view>
				</uni-list-item>
			</uni-list>
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
