<template>
	<view>
		<view style="padding: 20rpx; width: 100%; height: 300rpx; background: linear-gradient(180deg,#FFA755,#FF7BA5);position: absolute;">
			
			<view >
				<u-swiper :list="list" ></u-swiper>
			</view>
			<view style="margin-top: 50rpx;">
				<u-search />
			</view>
		</view>
		<view style="height: 10rpx;"></view>
		<view style="margin-top: 400rpx; padding: 20rpx;">
			<view>
				<u-subsection active-color="#FFA755" :list="slist" @change="chg"></u-subsection>
			</view>
			<view>
				<view @click="to(item.id)" v-for="item in ssslist" style="padding: 10rpx; width: 100%; margin-top: 20rpx; box-shadow: 0 0 20rpx #ccc; border-radius: 30rpx; display: flex;">
					<view style="width: 40%;">
						<image style="width: 100%; height: 250rpx; border-radius: 30rpx;" :src="gp()+item.pic" mode="scaleToFill"></image>
					</view>
					<view style="width: 60%; margin-left: 20rpx;">
						<view style="font-size: 35rpx; font-weight: bold;">{{item.sourceName}}</view>
						<view v-if="item.description" style="margin-top: 10rpx;">{{item.description.slice(0,10)}}...</view>
						<view style="margin-top: 10rpx;">面积:{{item.areaSize}}/平</view>
						<view style="margin-top: 10rpx;">价格:{{item.price}}</view>
					</view>
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
				slist:[{name:'二手'},{name:'租房'},{name:'楼盘'},{name:'中介'}],
				ssslist:[],
				sssslist:[]
			}
		},
		methods: {
			chg(e){
				this.ssslist = this.sssslist.filter(res=>{
					return res.houseType == this.slist[e].name
				})
			},
			to(e){
				uni.navigateTo({
					url: 'moreHo/moreHo?id='+e,
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/house/housing/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						for(let i of res.data.rows){
							this.list.push({
								image:this.gp()+i.pic
							})
						}
					}
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/api/house/housing/list',
				method: 'GET',
				data: {
					houseType:'二手'
				},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.ssslist = res.data.rows
					}
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/api/house/housing/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.sssslist = res.data.rows
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
