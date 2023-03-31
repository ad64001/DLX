<template>
	<view>
		<view style="padding: 20rpx; background: linear-gradient(180deg,#22c876,#00dee5); width: 100%; height: 300rpx; border-radius:  0 0 20rpx 20rpx; position: absolute;">
			<view>
				<u-search :action-style="{'color':'#fff'}" :input-style="{'background':'#fff'}" bgColor="#fff" borderColor="#fff"/>
			</view>
			<view style="margin-top: 20rpx;">
				<u-swiper :list="list"></u-swiper>
			</view>
			<view style="margin-top: 50rpx;">
				<view style="margin-bottom: 50rpx;">
					<u-section title="社区动态" lineColor="#22c876" :right="false" ></u-section>
				</view>
				<uni-list>
					<uni-list-item v-for="item in 4">
						<view slot="header">
							<image style="border-radius: 20rpx; width: 200rpx; height: 200rpx;" src="../../../../static/image/person.jpg" mode=""></image>
						</view>
						<view slot="body" style="margin-left: 20rpx; margin-top: 20rpx;">
							<view style="font-weight: bold;font-size: 35rpx;">物业通知</view>
							<view style="font-weight: bold;">示例动态</view>
							<view>示例动态示例动态示例动态示例动态示例动态示例动态示例动态示例动态示例动态</view>
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
								list:[{image:'../../../../static/image/banner2.jpg'},{image:'../../../../static/image/banner2.jpg'},{image:'../../../../static/image/banner2.jpg'}],
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
