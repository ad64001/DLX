<template>
	<view>
		<view>
			<view style="width: 100%; height: 60rpx; background: #0080f0;"></view>
			<uni-nav-bar left-icon="back" @clickLeft="toi()" right-icon="map" @clickRight="to()" title="城市地铁" backgroundColor="#0080f0" color="#fff"></uni-nav-bar>
		</view>
		<view style="padding: 20rpx;">
			<view style="display: flex;">
				<view style="display: flex; font-size: 30rpx; width: 25%; color: #0080f0;">
					<u-icon name="map" size="30"></u-icon><view style="margin: auto;">建国门</view>
				</view>
				<view style="width: 75%;">
					<uni-search-bar placeholder="输入你想去的站点" />
				</view>
				
			</view>
			<view>
				<view>
					<u-section title="地铁站点" lineColor="#1455ff" :right="false"></u-section>
				</view>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-card :isFull="true" style="border-radius: 30rpx; border: 1rpx solid #ccc; padding: 20rpx; ">
					<u-time-line>
						<u-time-line-item node-top="10" v-for="(item,index) in slist">
							<template v-slot:node>
								<view>
									<view style="width: 40rpx; height: 40rpx; border-radius: 100rpx; display: flex; align-items: center; justify-content: center; background: #02c39a;"></view>
								</view>
							</template>
							<template v-slot:content>
								<view style="margin-left: 20rpx;">
									<view style="color: #333333; font-weight: bold; font-size: 30rpx; color: #0080f0;">{{item.reachTime}}分钟</view>
									<view style="color: #333333; font-size: 30rpx;">下一站:{{item.nextStep.name}}</view>
									<navigator :url="'moreDXQ/moreDXQ?id='+item.lineId">
										<view style="color: gray; position: absolute; display: flex; right: 12rpx; top: 22rpx; font-size: 30rpx;" >
											<view>{{item.lineName}}</view>
											<view><u-icon name="arrow-right"></u-icon></view>
										</view>
									</navigator>
								</view>
							</template>
						</u-time-line-item>
					</u-time-line>
				</uni-card>
			</view>
		</view>
	</view>
	
</template>

<script>
	export default {
		data() {
			return {
				list:{},
				slist:[]
			}
		},
		methods: {
			to(){
				uni.navigateTo({
					url: '/pages/service/metro/moreDXQ/moreM',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			},
			toi(){
				uni.navigateBack({
					delta: 1
				});
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/common/gps/location',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.list = res.data.data
					}
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/api/metro/list',
				method: 'GET',
				data: {
					currentName:'建国门'
				},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.slist = res.data.data
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
	background: #F9F9F9;
}
</style>
