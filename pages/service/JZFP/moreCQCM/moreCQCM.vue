<template>
	<view>
		<view style="padding: 20rpx; background: linear-gradient(180deg,#F62D59,#FF2D69); width: 100%; height: 300rpx; border-radius:  0 0 20rpx 20rpx; position: absolute;">
			
			<view style="margin-top: 20rpx;">
				<u-swiper></u-swiper>
			</view>
			<view>
				<view style="margin-top: 50rpx;">
					<u-section title="贫困村" lineColor="#F62D59"  :right="false"></u-section>
				</view>
				
				<view style="margin-top: 20rpx;">
					<scroll-view scroll-x="true" style="white-space: nowrap; width: 100%;">
						<view style="display: flex;">
							<view style="margin-left: 30rpx; width: 750rpx; border-radius: 30rpx; border: 1rpx solid #ccc; padding: 10rpx;" v-for="item in 4">
								<navigator url="morePKCXQ" style="display: flex;">
									<view style="width: 40%;">
										<image style="border-radius: 20rpx; width: 300rpx; height: 200rpx; background: #ccc;" src="" mode=""></image>
									</view>
									<view  style="width: 55%; margin-left: 60rpx;">
										<view style="display: inline; font-size: 35rpx; font-weight: bold; word-break: break-all;">例示例示例例</view>
										<view>例示例示例例例示例示</view>
										<view style="display: flex;margin-top: 40rpx;">
											<view><u-icon name="eye"></u-icon>12</view>
											<view style="margin-left: 20rpx;"><u-icon name="chat"></u-icon>12</view>
											<view style="margin-left: 20rpx;"><u-icon name="thumb-up"></u-icon>12</view>
										</view>
										
										<view style="margin-top: 10rpx;">发布时间:114514-19-19</view>
									</view>
								</navigator>
							</view>
						</view>
					</scroll-view>
				</view>
			</view>
			<view style="margin-top: 20rpx;">
				<view style="margin-top: 50rpx;">
					<u-section title="扶贫新闻" lineColor="#F62D59"  :right="false"></u-section>
				</view>
				<view style="margin-top: 20rpx;">
					<u-subsection active-color="#F62D59" :list="slist"></u-subsection>
				</view>
				<view style="margin-top: 10rpx;">
					<uni-list>
						<uni-list-item v-for="item in 4" to="moreDJH/moreDJH">
							<view slot="header">
								<view style="font-size: 35rpx; font-weight: bold;word-break: break-all;">蘑菇屋是一款,用户可以定制合租室友，发布合租需求，还提供了众多生活服务，认识身边志趣相投的朋友</view>
								<view style="display: flex;margin-top: 10rpx;">
									<view><u-icon name="eye"></u-icon>12</view>
									<view style="margin-left: 20rpx;"><u-icon name="chat"></u-icon>123</view>
									<view style="margin-left: 20rpx;"><u-icon name="thumb-up"></u-icon>123</view>
								</view>
								
								<view style="margin-top: 10rpx;">发布时间:1919-12-15</view>
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
