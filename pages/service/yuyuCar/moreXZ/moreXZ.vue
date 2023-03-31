<template>
	<view>
		<view style="padding: 20rpx; width: 100%; height: 350rpx; background: linear-gradient(180deg,#00dee5,#00cee5); position: absolute;">
			<uni-group mode="card" margin-top="300rpx" style="height: 450rpx;" >
				<view @click="to">
					<view style="text-align: center;font-size: 35rpx;">预约须知</view>
					<view style="margin-top: 20rpx;">
						示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例
						示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例
						示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例
						示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例
						示例示例示例示例示例示例示例示例示例示例示例示例示例示例示例
						示例示例示例示例示例示例示例示例示例示例示例示例示例
						
					</view>
					
				</view>
			</uni-group>
		</view>
		<view style="position: fixed; bottom: 0; width: 100%; height: 150rpx; background: #fff;">
			<uni-grid :column="4" :showBorder="false" :highlight="false">
				<uni-grid-item>
					<view style="margin: auto;" @click="to(0)">
						<view style="display: flex; margin: auto;">
							<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../../static/icons/home_act.png" mode=""></image>
						</view>
						<view style="text-align: center; margin: 10rpx auto;">预约须知</view>
					</view>
				</uni-grid-item>
				<uni-grid-item>
					<view style="margin: auto;" @click="to(1)">
						<view style="display: flex; margin: auto;">
							<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../../static/icons/news.png" mode=""></image>
						</view>
						<view style="text-align: center; margin: 10rpx auto;">立即预约</view>
					</view>
				</uni-grid-item>
				<uni-grid-item>
					<view style="margin: auto;" @click="to(2)">
						<view style="display: flex; margin: auto;">
							<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../../static/icons/user.png" mode=""></image>
						</view>
						<view style="text-align: center; margin: 10rpx auto;">我的预约</view>
					</view>
				</uni-grid-item>
				<uni-grid-item>
					<view style="margin: auto;" @click="to(3)">
						<view style="display: flex; margin: auto;" >
							<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../../static/icons/all.png" mode=""></image>
						</view>
						<view style="text-align: center; margin: 10rpx auto;">车辆管理</view>
					</view>
				</uni-grid-item>
			</uni-grid>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				ssssslist:[]
			}
		},
		methods: {
			to(e){
				if(e == 1){
					uni.redirectTo({
						url: '/pages/service/yuyuCar/yuyuCar',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == 2){
					uni.redirectTo({
						url: '/pages/service/yuyuCar/moreWD/moreWD',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == 3){
					uni.redirectTo({
						url: '/pages/service/yuyuCar/moreCL/moreCL',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/traffic/checkCar/grt',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.ssssslist = res.data.data
					}
				},
				fail: () => {},
				complete: () => {}
			});
		}
	}
</script>

<style>
page{
	background: #f9f9f9;
}
</style>
