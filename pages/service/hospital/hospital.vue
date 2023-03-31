<template>
	<view>
		<view style="padding: 20rpx; width: 100%; height: 300rpx; border-radius: 0 0 100rpx 100rpx; background: linear-gradient(180deg,#22c786,#10aebe);">
			<view>
				<u-search :action-style="{'color':'#fff'}" :input-style="{'background':'#fff'}" bgColor="#fff" borderColor="#fff"/>
			</view>
			<view style="margin-top: 20rpx;">
				<u-swiper :list="list" ></u-swiper>
			</view>
		</view>
		<view style="height: 50rpx;"></view>
		<view style="margin-top: 20rpx; padding: 20rpx;">
			<view>
				<uni-grid :column="2" :showBorder="false" :highlight="false">
					<uni-grid-item style="height: 140rpx;">
						<navigator url="moreH/moreG">
							<view style="display: flex; margin: auto; text-align: center; width: 90%; height: 140rpx; border: 1rpx solid #22c786; font-size: 50rpx; color: #22c786;"><view style="margin: auto;"><u-icon name="edit-pen"></u-icon>预约挂号</view></view>
						</navigator>
					</uni-grid-item>
					<uni-grid-item style="height: 140rpx;">
						<navigator url="moreH/moreL">
							<view style="display: flex; margin: auto; text-align: center; width: 90%; height: 140rpx; border: 1rpx solid #10aebe; font-size: 50rpx; color: #10aebe;"><view style="margin: auto;"><u-icon name="list"></u-icon>问诊历史</view></view>
						</navigator>
					</uni-grid-item>
				</uni-grid>
			</view>
		</view>
		<view style="margin-top: 20rpx; padding: 20rpx;">
			<view> 
				<u-section title="知名医院" lineColor="#22c786" :right="false"></u-section>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-list>
					<uni-list-item v-for="item in slist" :to="'moreH/moreH?id='+item.id">
						<view slot="header">
							<image style="border-radius: 20rpx; width: 300rpx; height: 200rpx;" :src="gp()+item.imgUrl" mode=""></image>
						</view>
						<view slot="body" style="margin-left: 20rpx;">
							<view style="font-size: 35rpx; font-weight: bold;word-break: break-all;">{{item.hospitalName}}</view>
							<view style="display: flex;"><view v-html="item.brief.slice(0,15)"></view>...</view>
							<view style="margin-top: 5vh;">
								<u-rate :current="item.level"></u-rate>
							</view>
							
						</view>
					</uni-list-item>
				</uni-list>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[],
				slist:[]
			}
		},
		methods: {
			
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/hospital/banner/list',
				method: 'GET',
				data: {
					hospitalId:10
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
				url: this.gp()+'/prod-api/api/hospital/hospital/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.slist = res.data.rows.sort((a,b)=>{
							return b.level - a.level
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
