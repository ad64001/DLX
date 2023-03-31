<template>
	<view style="padding: 20rpx;">
		<view>
			<view>
				<u-swiper :list="list"></u-swiper>
			</view>
		</view>
		<view>
			<view style="margin-top: 50rpx;">
				<u-section title="推荐活动" lineColor="#F62D59"  :right="false"></u-section>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-grid :column="2"  :showBorder="false" :highlight="false">
					<uni-grid-item style="margin-top: 10rpx; margin-bottom: 20rpx;" v-for="(item,index) in 4" >
							<view style="width: 90%;height: 350rpx; box-shadow:0rpx 0rpx 20rpx #eee; border-radius: 40rpx; margin: auto;">
								<navigator style="width: 100%;height: 400rpx;border-radius: 40rpx;">
								<view>
									<image style="width: 100%; height: 200rpx;border-radius: 40rpx; background: #ccc;" src="" mode=""></image>
								</view>
								<view style="padding: 5rpx; word-break: break-all; font-weight: bold;">
									活动示例活动示例活动示例活动示例活动示例活动示例活动示例活动示例
								</view>
								</navigator>
							</view>
					</uni-grid-item>
				</uni-grid>
			</view>
		</view>
		<view>
			<view style="margin-top: 50rpx;">
				<u-section title="活动列表" lineColor="#F62D59"  :right="false"></u-section>
			</view>
			<view style="margin-top: 10rpx;">
				<uni-list>
					<uni-list-item v-for="item in 4">
						<view slot="header">
							<image style="width: 250rpx; height: 250rpx; background: #ccc; border-radius: 30rpx;" src="" mode=""></image>
						</view>
						<view slot="body" style="margin-left: 20rpx;">
							<view style="font-size: 35rpx; font-weight: bold;word-break: break-all;">习近平强军思想学习问答</view>
							<view style="word-break: break-all;">习近平强军思想学习问答习近平强军思想学习问答习近平强军思想学习问答</view>
							<view style="display: flex;margin-top: 10rpx;">
								<view><u-icon name="eye"></u-icon>12</view>
								<view style="margin-left: 20rpx;"><u-icon name="chat"></u-icon>123</view>
								<view style="margin-left: 20rpx;"><u-icon name="thumb-up"></u-icon>123</view>
							</view>
							<view><button @click="toBM" style="width: 150rpx; position: absolute; right: 12rpx; background: #F62D59; color: #fff; font-size: 25rpx;">报名</button></view>
						</view>
					</uni-list-item>
				</uni-list>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[{image:'../../../../static/image/studyImg.png'},{image:'../../../../static/image/studyImg.png'},{image:'../../../../static/image/studyImg.png'}]
			}
		},
		methods: {
			toBM(){
				uni.navigateTo({
					url: 'moreHDX',
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
