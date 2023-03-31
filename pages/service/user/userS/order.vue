<template>
	<view>
		<view style="width: 100%; position: fixed;">
			<u-subsection active-color="#ff9900" :list="list"></u-subsection>
		</view>
		<view style="height: 50rpx;"></view>
		<view style="margin-top: 20rpx;border: 1rpx solid #ccc;">
			<uni-list>
				<uni-list-item v-for="item in 4">
					<view slot="header">
						<view style="display: flex;">
							<view style="font-size: 35rpx; font-weight: bold;">商家</view>
							<view style="text-align: right; margin: auto; color: #ccc; position: absolute; right: 2vw;">已付款</view>
						</view>
						
						<view style="display: flex;margin-top: 10rpx;">
							订单编号
						</view>
						<view style="display: flex;margin-top: 10rpx;">
							订单类型
						</view>
						<view style="margin-top: 10rpx;">支付时间:{{item.publishDate}}</view>
					</view>
				</uni-list-item>
			</uni-list>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[{name:'已付款'},{name:'未付款'}],
				slist:[]
			}
		},
		methods: {
			
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/allorder/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.slist = res.data.rows
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
