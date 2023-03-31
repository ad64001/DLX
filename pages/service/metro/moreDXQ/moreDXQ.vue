<template>
	<view>
		<view style="padding: 20rpx;">
			
			<view style="margin-top: 20rpx;">
				<uni-card style="border: 1rpx solid #ccc; border-radius: 30rpx;" :isFull="true">
					<view>
						<u-section title="线路站点" lineColor="#1455ff" :right="false"></u-section>
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
					<view style="font-size: 35rpx; color: gray; display: flex; margin: auto; ">下一站<view style="font-weight: bold;">{{nextname}}</view>请做好准备</view>
				</uni-card>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-card style="border: 1rpx solid #ccc; border-radius: 30rpx; " :isFull="true">
					<view>
						<u-section title="途经站点" lineColor="#1455ff" :right="false"></u-section>
					</view>
					<view style="margin-top: 20rpx;">
						<scroll-view scroll-x="true" style="white-space: nowrap; width: 100%;">
							<view>
								<u-steps :list="sslist" :current="current" ></u-steps>
							</view>
						</scroll-view>
					</view>
					
				</uni-card>
				
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				slist:{},
				sslist:[],
				current:'',
				nextname:''
			}
		},
		methods: {
			toi(){
				uni.navigateBack({
					delta: 1
				});
			}
		},
		onLoad(e) {
			uni.request({
				url: this.gp()+'/prod-api/api/metro/line/'+e.id,
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.slist = res.data.data
						this.sslist = res.data.data.metroStepList
						for(let i = 0;i<res.data.data.metroStepList.length;i++){
							if(res.data.data.metroStepList[i].name.includes('建国门')){
								this.current = i
								this.nextname = res.data.data.metroStepList[i+1].name
							}
							
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
