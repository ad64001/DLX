<template>
	<view>
		<view style="padding: 20rpx;">
			<view>
				<u-section title="户号列表" lineColor="#0080f0" :right="false"></u-section>
			</view>
			<view>
				<view style="margin-top: 20rpx;">
					<uni-collapse>
						<uni-collapse-item title="朋友" style="background: #fff;">
							<uni-list>
								<uni-list-item v-for="item in 4">
									<view slot="header">
										<view style="font-size: 35rpx; font-weight: bold;word-break: break-all;">小明</view>
									</view>
									
								</uni-list-item>
							</uni-list>
						</uni-collapse-item>
					</uni-collapse>
					<view style="display: flex;">
						<u-field label="水费" placeholder="缴纳水费" />
						<view style="margin: auto;"> 412-3-3</view>
					</view>
			</view>
				<button @click="tl" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#00d0f0,#00a0f0); color: #fff; margin: 30rpx auto;">添加户号</button>
			</view>
			
			
		</view>
		<view>
			<view style="position: fixed; bottom: 0; width: 100%; height: 120rpx; background: #fff;">
				<uni-grid :column="2" :showBorder="false" :highlight="false">
					<uni-grid-item style="height: 150rpx;">
						<view style="margin: auto;" @click="to(0)">
							<view style="display: flex; margin: auto;">
								<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../../static/icons/news.png" mode=""></image>
							</view>
							<view style="text-align: center; margin: 10rpx auto;">自动缴费</view>
						</view>
					</uni-grid-item>
					<uni-grid-item style="height: 150rpx;">
						<view style="margin: auto;" @click="to(1)">
							<view style="display: flex; margin: auto;">
								<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../../static/icons/home_act.png" mode=""></image>
							</view>
							<view style="text-align: center; margin: 10rpx auto;">户号管理</view>
						</view>
					</uni-grid-item>
				</uni-grid>
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
			to(e){
				if(e == 0){
					uni.redirectTo({
						url: "/pages/service/living/living",
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}
			},
			tl(){
				uni.navigateTo({
					url: 'moreNH',
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
