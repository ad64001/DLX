<template>
	<view>
		<view style="padding: 20rpx;">
		
			<view style="margin-top: 20rpx;">
				<uni-card style="border: 1rpx solid #ccc; border-radius: 30rpx;" :isFull="true">
					<view>
						<u-section title="巴士站点" lineColor="#f62d59" :right="false"></u-section>
					</view>
					<view style="margin-top: 20rpx; width: 150rpx; height: 60rpx; display: flex; border:1rpx solid #F62D59; color: #F62D59; border-radius: 40rpx;">
						<view style="margin: auto; font-size: 40rpx; font-weight: bold;">{{slist.name}}</view>
					</view>
					<view style="width: 100%; display: flex; font-size: 45rpx; margin-top: 30rpx;">
						<view style="font-weight: bold;display:inline;margin-left: 20rpx;">
							{{slist.first}}
						</view>
						<view style="display: inline; margin: auto;">
							<u-icon name="arrow-rightward" size="60rpx"></u-icon>
						</view>
						<view style=" font-weight: bold;display:inline;margin: auto;">
							{{slist.end}}
						</view>
					</view>
					
					<view style="margin-top: 30rpx;">
						<view style="font-size: 30rpx; display: flex; margin: 10rpx auto auto 20rpx;">
							<view style="display: flex;"><view style=" background: #22c876; color: #fff; width: 40rpx; text-align: center; margin:auto 10rpx auto auto;">始</view><view style="margin:auto 30rpx auto auto;">{{slist.startTime}}</view></view>
							<view style="display: flex;margin-top: 10rpx;"><view style="background: #F62D59; color: #fff; width: 40rpx; text-align: center; margin: auto 10rpx auto auto;">终</view><view style=" margin:auto 30rpx auto auto;">{{slist.endTime}}</view></view>
						</view>
					</view>
				</uni-card>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-card style="border: 1rpx solid #ccc; border-radius: 30rpx; " :isFull="true">
					<view style="font-size: 35rpx; color: gray; display: flex; margin: auto; ">收费:{{slist.price}}元</view>
					<view style="font-size: 35rpx; color: gray; display: flex; margin: auto; ">里程:{{slist.mileage}}/km</view>
				</uni-card>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-card style="border: 1rpx solid #ccc; border-radius: 30rpx; " :isFull="true">
					<view>
						<u-section title="站点详情" lineColor="#f62d59" :right="false"></u-section>
					</view>
					<view style="margin-top: 20rpx;">
						<scroll-view scroll-x="true" style="white-space: nowrap; width: 100%;">
							<view>
								<u-steps :list="list" current="1" ></u-steps>
							</view>
						</scroll-view>
					</view>
					
				</uni-card>
			</view>
			
		</view>
		<view>
			<button @click="tos" style="position: fixed; bottom: 0; width: 100%; border-radius: 30rpx; background: linear-gradient(180deg,#F62D59,#FF2D69); color: #fff;">下一步</button>
		</view>
	</view>
	
</template>

<script>
	export default {
		data() {
			return {
				slist:{},
				list:[],
				id:''
			}
		},
		methods: {
			tos(){
				uni.navigateTo({
					url: 'moreBDD?id='+this.id,
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad(e) {
			this.id = e.id
			uni.request({
				url: this.gp()+'/prod-api/api/bus/line/'+e.id,
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.slist = res.data.data 
					}
					
					console.log(this.slist)
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/api/bus/stop/list',
				method: 'GET',
				data: {
					linesId:e.id
				},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.list = res.data.rows
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
