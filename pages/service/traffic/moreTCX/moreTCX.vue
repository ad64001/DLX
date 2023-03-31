<template>
	<view style="padding: 20rpx;">
		<view>
			<u-section title="违章列表" lineColor="#00dee5" :right="false"></u-section>
		</view>
		<view style="margin-top: 20rpx;">
			<view>
				<uni-card @click="tos" :isFull="true" title="处理状态: 已缴款" style="margin: 20rpx auto; border: 1rpx solid #ccc; border-radius: 30rpx;" v-for="(item,index) in 4">
					<view>
						<view>违法时间:xxxxx</view>
						<view>违章地点:xxxxx</view>
						<view>违章记分:xxxxx</view>
						<view>罚款金额:xxxxx</view>
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
				
			}
		},
		methods: {
			tos(){
				uni.navigateTo({
					url: 'moreTWXQ',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/traffic/illegal/list',
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
