<template>
	<view style="padding: 20rpx;">
		<view>
			<u-search/>
		</view>
		<view style="margin-top: 20rpx;">
			<u-swiper effect3d :list="list" ></u-swiper>
		</view>
		<view style="margin-top: 50rpx;">
			<u-tabs :list="sssslist" active-color="#0080f0" @change="cher" :current="current"></u-tabs>
		</view>
		<view style="margin-top: 10rpx;">
			<uni-list>
				<uni-list-item v-for="item in ssssslist" :to="'newsMore/newsMore?id='+item.id">
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
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[],
				sssslist:[],
				ssssslist:[],
				current:0
			}
		},
		methods: {
			cher(e){
				this.current = e
				uni.request({
					url: this.gp()+'/prod-api/press/press/list',
					method: 'GET',
					data: {
						type:this.sssslist[e].id
					},
					success: res => {
						if(res.data.code == 200){
							this.ssssslist = res.data.rows
						}
					},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/rotation/list',
				method: 'GET',
				data: {},
				success: res => {
					if(res.data.code == 200){
						for(let i of res.data.rows){
							this.list.push({
								image:this.gp()+i.advImg,
								id:i.id
							})
						}
					}
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/press/category/list',
				method: 'GET',
				data: {},
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
				url: this.gp()+'/prod-api/press/press/list',
				method: 'GET',
				data: {
					type:9
				},
				success: res => {
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

</style>
