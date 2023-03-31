<template>
	<view>
		<view style="z-index: -1; position: absolute; width: 100%; height: 300rpx; border-radius: 0 0 100rpx 100rpx; background: linear-gradient(180deg,#0080f0,#0090f0);"></view>
		<view style="padding: 20rpx;">
			<view>
				<u-search :action-style="{'color':'#fff'}" :input-style="{'background':'#fff'}" bgColor="#fff" borderColor="#fff"/>
			</view>
			<view style="margin-top: 20rpx;">
				<u-swiper :list="list" ></u-swiper>
			</view>
			<view style="margin-top: 50rpx;">
				<uni-grid :column="5" :showBorder="false" :highlight="false">
					<uni-grid-item v-for="item in slist.slice(0,9)">
						<view @click="tose(item.serviceName)">
							<view style="display: flex; margin: auto; width: 100rpx; height: 100rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 70rpx; height: 70rpx; background: #eee; " :src="gp()+item.imgUrl" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;">{{item.serviceName}}</view>
						</view>
					</uni-grid-item>
					<uni-grid-item>
						<view>
							<view style="display: flex; margin: auto; width: 100rpx; height: 100rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 70rpx; height: 70rpx; background: #eee; " src="../../static/icons/all_act.png" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;">更多服务</view>
						</view>
					</uni-grid-item>
					<uni-grid-item>
						<view @click="tose('智慧党建')">
							<view style="display: flex; margin: auto; width: 100rpx; height: 100rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 70rpx; height: 70rpx; background: #eee; " src="../../static/icons/all_act.png" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;">智慧党建</view>
						</view>
					</uni-grid-item>
					<uni-grid-item>
						<view @click="tose('智慧环保')">
							<view style="display: flex; margin: auto; width: 100rpx; height: 100rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 70rpx; height: 70rpx; background: #eee; " src="../../static/icons/all_act.png" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;">智慧环保</view>
						</view>
					</uni-grid-item>
					<uni-grid-item>
						<view @click="tose('精准扶贫')">
							<view style="display: flex; margin: auto; width: 100rpx; height: 100rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 70rpx; height: 70rpx; background: #eee; " src="../../static/icons/all_act.png" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;">精准扶贫</view>
						</view>
					</uni-grid-item>
					<uni-grid-item>
						<view @click="tose('智慧养老')">
							<view style="display: flex; margin: auto; width: 100rpx; height: 100rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 70rpx; height: 70rpx; background: #eee; " src="../../static/icons/all_act.png" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;">智慧养老</view>
						</view>
					</uni-grid-item>
					<uni-grid-item>
						<view @click="tose('智慧社区')">
							<view style="display: flex; margin: auto; width: 100rpx; height: 100rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 70rpx; height: 70rpx; background: #eee; " src="../../static/icons/all_act.png" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;">智慧社区</view>
						</view>
					</uni-grid-item>
				</uni-grid>
			</view>
			<view style="margin-top: 50rpx;">
				<view>
					<u-section title="今日热门" lineColor="#0080f0"></u-section>
				</view>
				<view style="margin-top: 20rpx;">
					<uni-grid :column="2"  :showBorder="false" :highlight="false">
						<uni-grid-item style="margin-top: 10rpx; margin-bottom: 60rpx;" v-for="item in ssslist.slice(0,4)">
								<view style="width: 90%;height: 400rpx; box-shadow:0rpx 0rpx 20rpx #eee; border-radius: 40rpx;">
									<navigator style="width: 100%;height: 400rpx;border-radius: 40rpx;" :url="'../service/news/newsMore/newsMore?id='+item.id">
									<view>
										<image style="width: 100%; height: 250rpx;border-radius: 40rpx;" :src="gp()+item.cover" mode=""></image>
									</view>
									<view style="padding: 5rpx; word-break: break-all; font-weight: bold;">
										{{item.title.slice(0,15)}}...
									</view>
									</navigator>
								</view>
							
						</uni-grid-item>
					</uni-grid>
				</view>
			</view>
			<view style="margin-top: 50rpx;">
				<u-tabs :list="sssslist" active-color="#0080f0" @change="cher" :current="current"></u-tabs>
			</view>
			<view style="margin-top: 10rpx;">
				<uni-list>
					<uni-list-item v-for="item in ssssslist" :to="'/pages/service/news/newsMore/newsMore?id='+item.id">
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
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[],
				slist:[],
				sslist:[],
				ssslist:[],
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
			},
			tose(e){
				if(e=="门诊预约"){
					uni.navigateTo({
						url: '/pages/service/hospital/hospital',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == '智慧党建'){
					uni.navigateTo({
						url: '/pages/service/danJ/danJ',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == '城市地铁'){
					uni.navigateTo({
						url: '/pages/service/metro/metro',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == '智慧环保'){
					uni.navigateTo({
						url: '/pages/service/ZHHB/ZHHB',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == '精准扶贫'){
					uni.navigateTo({
						url: '/pages/service/JZFP/JZFP',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == '智慧养老'){
					uni.navigateTo({
						url: '/pages/service/ZHYL/ZHYL',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == '智慧社区'){
					uni.navigateTo({
						url: '/pages/service/ZHSQ/ZHSQ',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}
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
				url: this.gp()+'/prod-api/api/service/list',
				method: 'GET',
				data: {},
				success: res => {
					// console.log(res)
					if(res.data.code == 200){
						this.slist = res.data.rows
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
						this.ssslist = res.data.rows
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
