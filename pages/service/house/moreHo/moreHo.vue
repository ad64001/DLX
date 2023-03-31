<template>
	<view style="padding: 20rpx;">
		<view >
			<image v-if="list.pic" style="width: 100%; border-radius: 30rpx;height: 300rpx;" :src="gp()+list.pic" mode="scaleToFill"></image>
			<image v-if="!list.pic" style="width: 100%; border-radius: 30rpx;height: 300rpx; background: #ccc;" src="" mode="scaleToFill"></image>
		</view>
		<view style="margin-top: 20rpx; display: flex;">
			<view style="font-size: 40rpx; font-weight: bold;">{{list.sourceName}}</view>
		</view>
		<view style="margin-top: 20rpx; display: flex;">
			<view style="font-size: 30rpx; color: #ccc;">{{list.address}}</view>
		</view>
		<view style="margin-top: 20rpx; display: flex;">
			<view style="font-size: 35rpx; color: gray;">面积:{{list.areaSize}}/平</view>
			<view style="font-size: 35rpx; margin-left: 25rpx;color: orangered;">价格:{{list.price}}</view>
		</view>
		<view style="margin-top: 30rpx;">
			<view>
				<u-section title="简介详情" lineColor="#FFA755" :right="false"></u-section>
			</view>
			<uni-card style="margin-top: 20rpx; border-radius: 30rpx; border: 1rpx solid #ccc;" :isFull="true">
				<view style="font-size: 30rpx; color: gray;">{{list.description}}</view>
			</uni-card>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:{}
			}
		},
		methods: {
			
		},
		onLoad(e) {
			uni.request({
				url: this.gp()+'/prod-api/api/house/housing/'+e.id,
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
		}
	}
</script>

<style>
page{
	background: #f9f9f9;
}
</style>
