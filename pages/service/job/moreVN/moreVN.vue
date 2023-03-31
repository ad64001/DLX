<template>
	<view>
		<view style="margin-top: 30rpx; padding: 20rpx;">
			<view>
				<u-section title="详情" lineColor="#00dee5" :right="false"></u-section>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-list style="border-radius: 30rpx;">
					<uni-list-item style="background: #f9f9f9;">
						<view slot="header">
							<view>公司地址:{{list.address}}</view>
						</view>
					</uni-list-item>
					
					<uni-list-item>
						<view slot="header">
							<view>联系人名称:{{list.contacts}}</view>
						</view>
					</uni-list-item>
					<uni-list-item style="background: #f9f9f9;">
						<view slot="header">
							<view>岗位名称:{{list.name}}</view>
						</view>
					</uni-list-item>
					<uni-list-item>
						<view slot="header">
							<view>岗位职责:{{list.obligation}}</view>
						</view>
					</uni-list-item>
					<uni-list-item style="background: #f9f9f9;">
						<view slot="header">
							<view>职位需求:{{list.need}}</view>
						</view>
					</uni-list-item>
					<uni-list-item>
						<view slot="header">
							<view>薪资待遇:{{list.salary}}元</view>
						</view>
					</uni-list-item>
				</uni-list>
			</view>
			
		</view>
		<button @click="tl" style="position: fixed; bottom: 0; border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#FFA755,#FF7BA5); color: #fff; margin: 30rpx auto;">投简历</button>
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
			tl(){
				let i = new Date().getFullYear()+'-'+new Date().getMonth()+'-'+new Date().getDay()+" "+new Date().getHours()+':'+new Date().getMinutes()+':'+new Date().getSeconds() 
				console.log(i)
				uni.request({
					url: this.gp()+'/prod-api/api/job/deliver',
					method: 'POST',
					data: {
						companyId:this.list.companyId,
						money:this.list.money,
						satrTime: i,
						postId: this.list.professionId,
						postName:this.list.name
					},
					header:this.th(),
					success: res1 => {
						console.log(res1)
						if(res1.data.code == 200){
							uni.navigateBack()
						}
					},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad(e) {
			uni.request({
				url: this.gp()+'/prod-api/api/job/post/'+e.id,
				method: 'GET',
				data: {},
				header:this.th(),
				success: res1 => {
					console.log(res1)
					if(res1.data.code == 200){
						this.list = res1.data.data
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
