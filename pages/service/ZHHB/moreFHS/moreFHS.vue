<template>
	<view style="padding: 20rpx;">
		<view>
			<image style="width: 100%; height: 600rpx; background: #ccc;" src="" mode="widthFix"></image>
		</view>
		<view>
			<view style="margin-top: 50rpx;">
				<u-section title="附近回收机" lineColor="#22c876" :right="false" ></u-section>
			</view>
			<view style="margin-top: 20rpx;">
				<scroll-view scroll-y="true" style="height: 600rpx; background: #fff;">
					<view>
						<uni-list>
							<uni-list-item v-for="item in 4">
								<view slot="header">
									<image style="border-radius: 20rpx; width: 200rpx; height: 100rpx;" src="" mode=""></image>
								</view>
								<view slot="body" style="margin-left: 20rpx;">
									<view style="font-size: 35rpx; font-weight: bold;word-break: break-all;">地址:汤臣一品</view>
									<view style="display: flex;">距离:114/m</view>
									<view style="margin-top: 10rpx;">回收类别:废电池</view>
								</view>
							</uni-list-item>
						</uni-list>
					</view>
				</scroll-view>
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
page{
	background: #f9f9f9;
}
</style>
