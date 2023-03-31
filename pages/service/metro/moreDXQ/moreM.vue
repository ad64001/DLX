<template>
	<view style="padding: 20rpx;">
		<view style="width: 100%; display: flex;">
			<view style="width: 35%; height: 500rpx; ">
				<scroll-view scroll-y="true" style="height: 90vh;">
					<view>
						<uni-list>
							<uni-list-item  v-for="(item,index) in list" :key="index" >
								<view slot="header">
									<view>{{item.lineName}}</view>
								</view>
							</uni-list-item>
						</uni-list>
					</view>
				</scroll-view>
				
			</view>
			<view style="width: 65%;">
				<view>
					<image style="width: 100%;" :src="gp()+slist.imgUrl" mode="widthFix"></image>
				</view>
			</view>
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
			
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/metro/city',
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
			uni.request({
				url: this.gp()+'/prod-api/api/metro/line/list',
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

</style>
