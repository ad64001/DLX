<template>
	<view>
		<view style="position: absolute; padding: 20rpx; width: 100%; height: 250rpx; background: linear-gradient(180deg,#00dee5,#00eee5);border-radius: 0 0 30rpx 30rpx;">
			<image style="width: 100%; height: 280rpx; background: #eee; border-radius: 30rpx;" src="" mode=""></image>
		</view>
		<view style="height: 15rpx;"></view>
		<view style="margin-top: 300rpx; padding: 20rpx;">
			<view>
				<u-section title="详情" lineColor="#00dee5" :right="false"></u-section>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-list style="border-radius: 30rpx;">
					<uni-list-item>
						<view slot="header">
							<view>停车场名称:{{slist.parkName}}</view>
						</view>
					</uni-list-item>
					<uni-list-item style="background: #f9f9f9;">
						<view slot="header">
							<view>地址:{{slist.address}}</view>
						</view>
					</uni-list-item>
					
					<uni-list-item>
						<view slot="header">
							<view>空位个数:{{slist.vacancy}}</view>
						</view>
					</uni-list-item>
					<uni-list-item style="background: #f9f9f9;">
						<view slot="header">
							<view>对外开放:{{slist.open == "Y" ? '开放' : '关闭'}}</view>
						</view>
					</uni-list-item>
					<uni-list-item>
						<view slot="header">
							<view>收费:{{slist.rates}}元/h</view>
						</view>
					</uni-list-item>
					<uni-list-item style="background: #f9f9f9;">
						<view slot="header">
							<view>一天收费:{{slist.priceCaps}}/元</view>
						</view>
					</uni-list-item>
				</uni-list>
				<view style=" justify-content: center; align-items: center; font-size: 45rpx; font-weight: bold; width: 100%; height: 400rpx; display: flex; background: #fff; color: #ff9214;">
					欢迎光临{{slist.parkName}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				slist:{}
			}
		},
		methods: {
			
		},
		onLoad(e) {
			uni.request({
				url: this.gp()+'/prod-api/api/park/lot/'+e.id,
				method: 'GET',
				data: {},
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
	background: #f9f9f9;
}
</style>
