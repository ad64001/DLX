<template>
	<view>
		<view style="padding: 20rpx; background: linear-gradient(180deg,#F62D59,#FF2D69); width: 100%; height: 300rpx; border-radius:  0 0 20rpx 20rpx; position: absolute;">
			
			<view style="margin-top: 20rpx;">
				<u-swiper></u-swiper>
			</view>
			
			<view style="margin-top: 20rpx;">
				<view style="margin-top: 50rpx;">
					<u-section title="住户列表" lineColor="#F62D59"  :right="false"></u-section>
				</view>

				<view style="margin-top: 10rpx;">
					<uni-list>
						<uni-list-item v-for="item in 4" to="moreZHXQ">
							<view slot="header">
								<view style="font-size: 35rpx; font-weight: bold;word-break: break-all;">住户名称</view>
								<view>账户详情:示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例</view>
							</view>
						</uni-list-item>
					</uni-list>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				slist:[{name:'共产党'},{name:'热点新闻'},{name:'扶贫成果'}]
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
