<template>
	<view>
		<view style="padding: 20rpx;">
			<view>
				<u-swiper :list="list" height="350" effect3d></u-swiper>
			</view>
			<view style="margin-top: 20rpx; font-weight: bold; font-size: 45rpx; ">
				{{slist.hospitalName}}
			</view>
			<view style="margin-top: 20rpx;">
				<u-section title="医院简介" lineColor="#22c786" :right="false"></u-section>
			</view>
			<uni-card style="border-radius: 20rpx; margin-top: 20rpx;" :isFull="true">
				<view v-html="slist.brief"></view>
			</uni-card>
			
		</view>
		<view style="width: 100%; position: fixed; bottom: 0;">
			<button @click="toY" style="background: linear-gradient(90deg,#22c786,#10aebe); color: #fff;">预约挂号</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[],
				slist:{}
			}
		},
		methods: {
			toY(){
				uni.navigateTo({
					url: 'moreY',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad(e) {
			uni.request({
				url: this.gp()+'/prod-api/api/hospital/banner/list',
				method: 'GET',
				data: {
					hospitalId:e.id
				},
				header:this.th(),
				success: res => {
					if(res.data.code == 200){
						for(let i of res.data.data){
							this.list.push({
								image:this.gp()+i.imgUrl,
								id:i.id
							})
						}
					}
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/api/hospital/hospital/'+e.id,
				method: 'GET',
				data: {},
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

</style>
