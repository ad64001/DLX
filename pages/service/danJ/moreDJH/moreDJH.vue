<template>
	<view style="padding: 20rpx;">
		<view>
			<image style="width: 100%; height: 300rpx;" src="../../../../static/image/studyImg.png" mode="scaleToFill"></image>
		</view>
		<view style="margin-top: 20rpx;">
			<uni-card :isFull="true" style="border-radius: 30rpx; border: 1rpx solid #ccc;">
				<view style="font-size: 40rpx;font-weight: bold;">示例示例示例示例</view>
				<view style="margin-top: 20rpx;">
					<u-section title="新闻详情" lineColor="#F62D59" :right="false"></u-section>
				</view>
				<view style="margin-top: 10rpx; text-indent: 2em; color: gray; word-break: break-all;">
					示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例
					示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例
					示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示
					例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例
				</view>
			</uni-card>
			<view style="margin-top: 20rpx;">
				<view style="margin-top: 20rpx;">
					<u-section title="评论区" lineColor="#F62D59" :right="false"></u-section>
				</view>
				<view style="margin-top: 20rpx;">
					<uni-list>
						<uni-list-item v-for="item in 4">
							<view slot="header">
								<image style="border-radius: 100rpx; width: 200rpx; height: 200rpx; background: #eee;" src="" mode=""></image>
							</view>
							<view slot="body" style="margin-left: 20rpx;">
								<view style="font-size: 35rpx; font-weight: bold;word-break: break-all;">示例</view>
								<view style="margin-top: 20rpx;">示例</view>
								<view style="display: flex;margin-top: 30rpx;">
									<view><u-icon name="thumb-up"></u-icon>114514</view>
								</view>
								
								<view>评论时间:1919-45-12</view>
							</view>
						</uni-list-item>
					</uni-list>
				</view>
				<view style="margin-top: 10rpx;">
					<uni-pagination total="114" current="1"></uni-pagination>
				</view>
				<view style="height: 100rpx;"></view>
			</view>
			
		</view>
		<view style="padding: 10rpx; position: fixed; bottom: 0; width: 100%; height: 100rpx; background: #fff; z-index: 99;padding: 10rpx; display: flex;">
			<u-icon name="order" size="65"></u-icon>
			<input type="text" style="padding: 4rpx; border-radius: 30rpx; border: #ccc; border: 1rpx solid #eee; width: 65%; height: 80rpx; margin: auto;" />
			<view style="font-size: 35rpx; font-weight: bold; margin: auto;">发送</view>
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
