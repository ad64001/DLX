<template>
	<view>
		<view>
			<view style="padding: 20rpx;">
				<view>
					<uni-group style="padding: 10rpx;" margin-top="20" mode="card" v-for="(item,index) in 4">
						<view>
							<view style="font-weight: bold; font-size: 35rpx; margin-bottom: 10rpx;">车牌号:辽 B12345</view>
							<u-line></u-line>
							<view style="margin-top: 20rpx;">预约时间：2020-10-24</view>
							<view style="margin-top: 20rpx;">车架：EWX1383E3J9491U</view>
							<view style="margin-top: 20rpx;">预约地址：丰台区潘北昊盛汽车检测有限公司</view>
							<view style="margin-top: 20rpx;">电话号码：11451419192</view>
						</view>
					</uni-group>
				</view>
			</view>
			<view style="height: 150rpx;"></view>
		</view>
		<view style="position: fixed; bottom: 0; width: 100%; height: 150rpx; background: #fff;">
			<uni-grid :column="4" :showBorder="false" :highlight="false">
				<uni-grid-item>
					<view style="margin: auto;" @click="to(0)">
						<view style="display: flex; margin: auto;">
							<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../../static/icons/home.png" mode=""></image>
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
							<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../../static/icons/user_act.png" mode=""></image>
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
				}else if(e == 0){
					uni.redirectTo({
						url: '/pages/service/yuyuCar/moreXZ/moreXZ',
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
				url: this.gp()+'/prod-api/api/traffic/checkCar/apply/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						
					}
				},
				fail: () => {},
				complete: () => {}
			});
		}
	}
</script>

<style>

</style>
