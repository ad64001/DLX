<template>
	<view>
		<view style="position: fixed; width: 100%; top: 0; z-index: 99;">
			<view style="width: 100%; height: 60rpx; background: #0080f0;"></view>
			<uni-nav-bar left-icon="location" left-text="北京" rightWidth="200" @clickLeft="" right-icon="forward" @clickRight="back" title="生活缴费" backgroundColor="#0080f0" color="#fff"></uni-nav-bar>
		</view>
		<view style=" 10%; padding: 20rpx; width: 100%; height: 300rpx; margin-top: 100rpx; background: linear-gradient(180deg,#0080f0,#009ff0); border-radius: 0 0 30rpx 30rpx;">
			<view style="height: 15rpx;"></view>
			<view style="margin-top: 40rpx;">
				<u-swiper :list="list"></u-swiper>
			</view> 
		</view>
		<view style="height: 15rpx;"></view>
		<view style="margin-top: 40rpx; padding: 20rpx;">
			<view style="padding: 20rpx; width: 100%; height: 450rpx; background: #0080f0; border-radius: 30rpx;">
				<text style="width: 300rpx; color: #fff;margin-top: 30rpx; font-weight: bold; margin-left: 50rpx; font-size: 75rpx; text-shadow: 40rpx 30rpx 10rpx #ccc;">缴费服务</text>
				<view style="width: 100%; height: 350rpx; background: #fff; border-radius: 30rpx; margin: 30rpx auto;">
					<uni-grid :column="2" :show-border="false" :highlight="false">
						<uni-grid-item style="height: 350rpx;"  v-for="(item,index) in slist.slice(1,3)">
							<view style="width: 100%; margin: auto;" @click="gt(item.liveName)">
								<view style="background: #f9f9f9; margin-top: 70rpx; border-radius: 100rpx; width: 150rpx; height: 150rpx; margin: auto; display: flex;">
									<image style="width: 100rpx; height: 100rpx; border-radius: 100rpx; margin: auto;" :src="gp()+item.imgUrl" mode=""></image>
								</view>
								<view style="margin: auto; text-align: center; font-size: 35rpx;">
									{{item.liveName}}
								</view>
							</view>
						</uni-grid-item>
					</uni-grid>
					
				</view>
			</view>
			
		</view>
		<view style="margin-top: 50rpx;">
			<u-tabs :list="sssslist" gutter="45" :show-bar="false" active-color="#0080f0" @change="cher" :current="current"></u-tabs>
		</view>
		<view>
			<uni-list>
				<uni-list-item v-for="item in ssssslist">
					<view slot="header">
						<image style="border-radius: 20rpx; width: 300rpx; height: 200rpx;" :src="gp()+item.cover" mode=""></image>
					</view>
					<view slot="body" style="margin-left: 20rpx;">
						<view style="font-size: 35rpx; font-weight: bold;word-break: break-all;">{{item.title.slice(0,15)}}...</view>
						<view style="display: flex;"><view v-html="item.content.slice(0,10)"></view>...</view>
						<view style="display: flex;margin-top: 10rpx;">
							<view><u-icon name="eye"></u-icon>{{item.readNum}}</view>
							<view style="margin-left: 20rpx;"><u-icon name="chat"></u-icon>{{item.commentNum}}</view>
							<view style="margin-left: 20rpx;"><u-icon name="thumb-up"></u-icon>{{item.likeNum}}</view>
						</view>
						
						<view style="margin-top: 10rpx;">发布时间:{{item.publishDate}}</view>
					</view>
				</uni-list-item>
			</uni-list>
		</view>
		<view style="height: 150rpx;"></view>
		<view>
			<view style="position: fixed; bottom: 0; width: 100%; height: 120rpx; background: #fff;">
				<uni-grid :column="2" :showBorder="false" :highlight="false">
					<uni-grid-item style="height: 150rpx;">
						<view style="margin: auto;" @click="to(0)">
							<view style="display: flex; margin: auto;">
								<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../static/icons/news_act.png" mode=""></image>
							</view>
							<view style="text-align: center; margin: 10rpx auto;">自动缴费</view>
						</view>
					</uni-grid-item>
					<uni-grid-item style="height: 150rpx;">
						<view style="margin: auto;" @click="to(1)">
							<view style="display: flex; margin: auto;">
								<image style=" width: 50rpx; height: 50rpx; margin: auto;" src="../../../static/icons/home.png" mode=""></image>
							</view>
							<view style="text-align: center; margin: 10rpx auto;">户号管理</view>
						</view>
					</uni-grid-item>
				</uni-grid>
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
				sssslist:[],
				current:0,
				ssssslist:[],
				ssslist:[]
			}
		},
		methods: {
			cher(e){
				this.current = e
				uni.request({
					url: this.gp()+'/prod-api/api/living/press/press/list',
					method: 'GET',
					data: {
						type:this.sssslist[e].id
					},
					header:this.th(),
					success: res => {
						console.log(res)
						if(res.data.code == 200){
							this.ssssslist = res.data.rows
						}
					},
					fail: () => {},
					complete: () => {}
				});
			},
			to(e){
				if(e == 1){
					uni.redirectTo({
						url: 'moreHH/moreHH',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}
			},
			back(){
				uni.navigateBack({
					delta: 1
				});
			},
			gt(e){
				if(e=="水费"){
					uni.navigateTo({
						url: '/pages/service/living/moreSD/moreSD',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else{
					uni.navigateTo({
						url: '/pages/service/living/moreSD/moreDF',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/living/rotation/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						for (let s of res.data.rows) {
							this.list.push({
								image:this.gp()+s.advImg
							})
						}
					}
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/api/living/category/list',
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
				url: this.gp()+'/prod-api/api/living/press/category/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.sssslist = res.data.data
					}
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/api/living/press/press/list',
				method: 'GET',
				data: {
					type:26
				},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.ssssslist = res.data.rows
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
