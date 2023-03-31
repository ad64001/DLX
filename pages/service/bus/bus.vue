<template>
	<view>
		<view style="padding: 20rpx;">
			<view style="">
				<u-section title="巴士列表" lineColor="#F62D59" :right="false"></u-section>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-card style="padding: 20rpx; border: 1rpx solid #ccc; border-radius: 30rpx; margin-top: 20rpx;" :isFull="true" v-for="(item,index) in list" :key="index">
					<view style="font-size: 35rpx; font-weight: bold; ">
						{{item.name}}
					</view>
					<u-line margin="10rpx"></u-line>
					<view style="width: 100%; display: flex; font-size: 45rpx; margin-top: 30rpx;">
						<view style="font-weight: bold;display:inline;margin-left: 20rpx;">
							{{item.first}}
						</view>
						<view style="display: inline; margin: auto;">
							<u-icon name="arrow-rightward" size="60rpx"></u-icon>
						</view>
						<view style=" font-weight: bold;display:inline;margin: auto;">
							{{item.end}}
						</view>
					</view>
					<view style="margin-top: 30rpx;">
						<view style="font-size: 30rpx; display: flex; margin: 10rpx auto auto 20rpx;">
							<view style="display: flex;"><view style=" background: #22c876; color: #fff; width: 40rpx; text-align: center; margin:auto 10rpx auto auto;">始</view><view style="margin:auto 30rpx auto auto;">{{item.startTime}}</view></view>
							<view style="display: flex;margin-top: 10rpx;"><view style="background: #F62D59; color: #fff; width: 40rpx; text-align: center; margin: auto 10rpx auto auto;">终</view><view style=" margin:auto 30rpx auto auto;">{{item.endTime}}</view></view>
						</view>
					</view>
					<view style="margin-top: 30rpx;">
						<view style="font-size: 30rpx; display: flex; margin: 10rpx auto auto 20rpx;">
							<view>票价:{{item.price}}元</view>
							<view style="margin-left: 50rpx;">里程:{{item.mileage}}/km</view>
						</view>
					</view>
					
					<view style="margin-top: 30rpx;">
						<uni-collapse>
							<uni-collapse-item style="background: #fff;" title="">
								<view style="height: 320rpx; ">
									<scroll-view scroll-y="true" style="height: 100%;">
										<view>
											<u-time-line style="margin-left: 50rpx; margin-bottom: 10rpx;">
												<u-time-line-item node-top="10" v-for="(item1,index1) in gets(item.id)">
													<template v-slot:node>
														<view>
															<view style="width: 40rpx; height: 40rpx; border-radius: 100rpx; display: flex; align-items: center; justify-content: center; background: #02c39a;"></view>
														</view>
													</template>
													<template v-slot:content>
														<view style="margin-left: 20rpx;">
															<view style="color: #333333; font-size: 30rpx;">站点:{{item1.name}}</view>
														</view>
													</template>
												</u-time-line-item>
											</u-time-line>
										</view>
									</scroll-view>
								</view>
							</uni-collapse-item>
						</uni-collapse>
					</view>
					<view style="text-align: right; color: #666666; font-size: 30rpx; margin-top: 20rpx;" @click="to(item.id)">查看详情<u-icon name="arrow-right-double"></u-icon></view>
				</uni-card>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[],
				slist:[],
				sslist:[]
	
			}
		},
		methods: {
			rt(){
				console.log(this.slist)
			},
			gets(e){
				return this.slist.filter(res=>{
					return res.linesId == e
				})
			},
			to(e){
				uni.navigateTo({
					url: '/pages/service/bus/moreBX/moreBX?id='+e,
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/bus/line/list',
				method: 'GET',
				data: {},
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.list = res.data.rows
					}
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/api/bus/stop/list',
				method: 'GET',
				data: {},
				success: res1 => {
					this.slist = res1.data.rows
				},
				fail: () => {},
				complete: () => {}
			});
		}
	}
</script>

<style>

</style>
