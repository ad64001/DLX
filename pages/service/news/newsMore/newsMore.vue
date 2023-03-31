<template>
	<view>
		<view style="padding: 20rpx;">
			<view style="font-size: 45rpx; font-weight: bold; word-break: break-all; text-align: center;">{{list.title}}</view>
			<view style="margin-top: 20rpx;">发布日期:{{list.publishDate}}</view>
			<view style="display: flex;margin-top: 20rpx;">
				<view><u-icon name="eye"></u-icon>{{list.readNum}}</view>
				<view style="margin-left: 20rpx;"><u-icon name="chat"></u-icon>{{commentNum}}</view>
				<view style="margin-left: 20rpx;"><u-icon name="thumb-up" @click="tolike(-1)"></u-icon>{{likeNum}}</view>
			</view>
			<view style="margin-top: 20rpx;">
				<image style="width: 100%; height: 280rpx; border-radius: 20rpx;" :src="gp()+list.cover" mode="scaleToFill"></image>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-card style="border-radius: 20rpx;" :isFull="true">
					<view v-html="list.content"></view>
				</uni-card>
			</view>
			<view style="margin-top: 20rpx;">
				<view>
					<u-section title="推荐新闻" lineColor="#0080f0" :right="false"></u-section>
				</view>
				<view style="margin-top: 20rpx;">
					<uni-list>
						<uni-list-item v-for="item in sslist.slice(0,3)" :to="'newsMore?id='+item.id" link="redirectTo">
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
			<view style="margin-top: 20rpx;">
				<view>
					<u-section :title="'评论数:'+commentNum" lineColor="#0080f0" :right="false"></u-section>
				</view>
				<view style="margin-top: 20rpx;">
					<uni-list>
						<uni-list-item v-for="item in ssslist.slice(ind,indes)">
							<view slot="header">
								<image style="border-radius: 100rpx; width: 200rpx; height: 200rpx; background: #eee;" src="" mode=""></image>
							</view>
							<view slot="body" style="margin-left: 20rpx;">
								<view style="font-size: 35rpx; font-weight: bold;word-break: break-all;">{{item.userName}}</view>
								<view style="margin-top: 20rpx;">{{item.content}}</view>
								<view style="display: flex;margin-top: 30rpx;">
									<view><u-icon name="thumb-up" @click="tolike(item.id)"></u-icon>{{item.likeNum}}</view>
								</view>
								
								<view>评论时间:{{item.commentDate}}</view>
							</view>
						</uni-list-item>
					</uni-list>
				</view>
				<view style="margin-top: 10rpx;">
					<uni-pagination :total="ssslist.length" current="1" @change="che"></uni-pagination>
				</view>
			</view>
			<view style="height: 100rpx;"></view>
		</view>
		<view style="position: fixed; bottom: 0; width: 100%; height: 100rpx; background: #fff; z-index: 99;padding: 10rpx; display: flex;">
			<u-icon name="order" size="70"></u-icon>
			<input v-model="msg" type="text" style="padding: 4rpx; border-radius: 30rpx; border: #ccc; border: 1rpx solid #eee; width: 75%; height: 80rpx; margin: auto;" />
			<view @click="tochat" style="font-size: 35rpx; font-weight: bold; margin: auto;">发送</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:{},
				commentNum:0,
				likeNum:0,
				sslist:[],
				ssslist:[],
				ind:0,
				indes:15,
				msg:'',
				id:''
				
			}
		},
		methods: {
			che(e){
				if(e.type == 'next'){
					this.ind += 5
					this.indes += 5
				}else{
					this.ind -= 5
					this.indes -= 5
				}
			},
			tochat(){
				uni.request({
					url: this.gp()+'/prod-api/press/pressComment',
					method: 'POST',
					data: {
						"newsId": this.id,
						"content": this.msg
					},
					header:this.th(),
					success: res => {
						console.log(res)
						if(res.data.code == 200){
							this.msg = ""
							uni.request({
								url: this.gp()+'/prod-api/press/press/'+this.id,
								method: 'GET',
								data: {},
								header:this.th(),
								success: res => {
									if(res.data.code == 200){
										this.commentNum = res.data.data.commentNum
									}
								},
								fail: () => {},
								complete: () => {}
							});
						}
					},
					fail: () => {},
					complete: () => {}
				});
			},
			tolike(e){
				if(e == -1){
					uni.request({
						url: this.gp()+'/prod-api/press/press/like/'+this.id,
						method: 'PUT',
						data: {},
						header:this.th(),
						success: res => {
							console.log(res)
							if(res.data.code == 200){
								uni.request({
									url: this.gp()+'/prod-api/press/press/'+this.id,
									method: 'GET',
									data: {},
									header:this.th(),
									success: res => {
										if(res.data.code == 200){
											this.likeNum = res.data.data.likeNum
										}
									},
									fail: () => {},
									complete: () => {}
								});
							}
						},
						fail: () => {},
						complete: () => {}
					});
				}else{
					uni.request({
						url: this.gp()+'/prod-api/press/pressComment/like/'+e,
						method: 'PUT',
						data: {},
						header:this.th(),
						success: res => {
							console.log(res)
							if(res.data.code == 200){
								uni.request({
									url: this.gp()+'/prod-api/press/comments/list',
									method: 'GET',
									data: {},
									success: res => {
										if(res.data.code == 200){
											this.ssslist = res.data.rows
										}
									},
									fail: () => {},
									complete: () => {}
								});
								
							}
						},
						fail: () => {},
						complete: () => {}
					});
				}
			}
		},
		onLoad(e) {
			this.id = e.id
			uni.request({
				url: this.gp()+'/prod-api/press/press/'+e.id,
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					if(res.data.code == 200){
						this.list = res.data.data
						this.commentNum = res.data.data.commentNum
						this.likeNum = res.data.data.likeNum
					}
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/press/press/list',
				method: 'GET',
				data: {},
				success: res => {
					if(res.data.code == 200){
						this.sslist = res.data.rows
					}
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/press/comments/list',
				method: 'GET',
				data: {
					newsId:e.id
				},
				success: res => {
					if(res.data.code == 200){
						this.ssslist = res.data.rows
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
