<template>
	<view>
		<view style="position: fixed; width: 100%; z-index: 99;top:0;">
			<view style="width: 100%; height: 60rpx; background: #00dee5;"></view>
			<uni-nav-bar left-icon="back" @clickLeft="toi()" right-icon="list" @clickRight="to()" title="停哪儿" backgroundColor="#00dee5" color="#fff"></uni-nav-bar>
		</view>
		<view style="margin-top: 130rpx; padding: 20rpx; width: 100%; height: 300rpx; background: linear-gradient(180deg,#00dee5,#00eee5);border-radius: 0 0 30rpx 30rpx;">
			<view>
				<u-search :action-style="{'color':'#fff'}" :input-style="{'background':'#fff'}" bgColor="#fff" borderColor="#fff"/>
			</view>
			<view style="margin-top: 20rpx;">
				<u-swiper :list="list" ></u-swiper>
			</view>
		</view>
		<view style="height: 15rpx;"></view>
		<view style="margin-top: 60rpx; padding: 20rpx;">
			<view>
				<u-section title="停车场" lineColor="#00dee5" :right="false"></u-section>
			</view>
			<view style="margin-top: 30rpx;">
				<uni-card @click="tops(item.id)" style="margin-top: 20rpx; border: 1rpx solid #ccc; border-radius: 20rpx; " :isFull="true" :note="'地址:'+item.address" v-for="(item,index) in slist.slice(0,inds)">
					<view style="font-size: 35rpx; font-weight: bold; color: #333333;">{{item.parkName}}</view>
					<u-line margin="10rpx"></u-line>
					<view style="width: 100%; display: flex;">
						<view style="width: 40%;">
							<image style="width: 300rpx;height: 200rpx; background: #eee;" :src="gp()+item.imgUrl" mode="scaleToFill"></image>
						</view>
						<view style="width: 60%; margin-left: 60rpx; font-size: 35rpx;">
							<view style="color: #ff9214;">收费:{{item.rates}}</view>
							<view style="color: #00dee5;">距离:{{item.distance}}/M</view>
							<view style="color: #1482ff;">空位个数:{{item.vacancy}}</view>
							<view style="color: #ff3014;">对外开放:{{item.open == "Y" ? '开放' : '关闭'}}</view>
						</view>
					</view>
				</uni-card>
			</view>
			<view style="margin-top: 20rpx;">
				<button v-show="inds < slist.length - 1" @click="tot" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#00dee5,#00eee5); color: #fff; margin: 30rpx auto;">加载更多</button>
				<u-divider v-show="inds > slist.length - 1">没有更多</u-divider>
			</view>
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[],
				slist:[],
				inds:6
			}
		},
		methods: {
			toi(){
				uni.navigateBack({
					delta: 1
				});
			},
			tops(e){
				uni.navigateTo({
					url: 'moreP/moreP?id='+e,
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			},
			tot(){
				this.inds += 5
			},
			to(){
				uni.navigateTo({
					url: 'moreP/moreT',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/park/rotation/list',
				method: 'GET',
				data: {},
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						 for(let i of res.data.rows){
							 this.list.push({
								 image:this.gp()+i.advImg
							 })
						 }
					}
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/api/park/lot/list',
				method: 'GET',
				data: {},
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						 this.slist = res.data.rows.sort((a,b)=>{
							 return a.distance - b.distance
						 })
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
