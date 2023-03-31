<template>
	<view>
		<view style="padding: 20rpx;">
			<view>
				<uni-group style="padding: 10rpx;" margin-top="20" mode="card" v-for="(item,index) in list">
					<view>
						<view style="position: absolute;right: 100rpx;">
							<u-checkbox-group>
									<u-checkbox @change="cge" v-model="item.che"/>
							</u-checkbox-group>
							</view>
						<view style="font-weight: bold; font-size: 35rpx; margin-bottom: 10rpx;">车牌号:{{item.plateNo}}</view>
						<u-line></u-line>
						<view style="margin-top: 20rpx;">车架号：{{item.engineNo}}</view>
						<view style="margin-top: 20rpx;">车辆类型：{{item.type}}</view>
						<view style="margin-top: 20rpx;">公里数：114514/km</view>
						<view style="margin-top: 20rpx;">电话号码：11451419192</view>
					</view>
				</uni-group>
			</view>
			<view><button @click="tos(0)" style="background: linear-gradient(180deg,#00dee5,#00eee5); color: #fff;">预约检车</button></view>
		</view>
		<view style="height: 150rpx;"></view>

		
		<view style="position: fixed; bottom: 0; width: 100%; height: 150rpx; background: #fff;">
			<uni-grid :column="4" :showBorder="false" :highlight="false">
				<uni-grid-item>
					<view style="margin: auto;" @click="to(0)">
						<view style="display: flex; margin: auto;">
							<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../static/icons/home.png" mode=""></image>
						</view>
						<view style="text-align: center; margin: 10rpx auto;">预约须知</view>
					</view>
				</uni-grid-item>
				<uni-grid-item>
					<view style="margin: auto;" @click="to(1)">
						<view style="display: flex; margin: auto;">
							<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../static/icons/news_act.png" mode=""></image>
						</view>
						<view style="text-align: center; margin: 10rpx auto;">立即预约</view>
					</view>
				</uni-grid-item>
				<uni-grid-item>
					<view style="margin: auto;" @click="to(2)">
						<view style="display: flex; margin: auto;">
							<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../static/icons/user.png" mode=""></image>
						</view>
						<view style="text-align: center; margin: 10rpx auto;">我的预约</view>
					</view>
				</uni-grid-item>
				<uni-grid-item>
					<view style="margin: auto;" @click="to(3)">
						<view style="display: flex; margin: auto;" >
							<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../static/icons/all.png" mode=""></image>
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
				list:[],
				checked:false
			}
		},
		methods: {
			to(e){
				if(e == 0){
					uni.redirectTo({
						url: '/pages/service/yuyuCar/moreXZ/moreXZ',
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
			},
			cge(e){
				
			},
			tos(){
				uni.navigateTo({
					url: 'moreXZ/moreYY',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
			
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/traffic/car/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						for(let i of res.data.rows){
							this.list.push({
								plateNo:i.plateNo,
								engineNo:i.engineNo,
								type:i.type,
								che:false,
								id:i.id
							})
						}
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
