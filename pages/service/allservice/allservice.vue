<template>
	<view style="padding: 20rpx;">
		<view>
			<u-search @custom="seart()" @search="seart()" v-model="msg"/>
		</view>
		<view style="width: 100%; display: flex; margin-top: 20rpx;">
			<view style="width: 30%;">
				<uni-list>
					<uni-list-item  v-for="(item,index) in list" :key="index" >
						<view slot="header" @click="toi(index)">
							<view :class="index == current?'aut':''">{{item.name}}</view>
						</view>
					</uni-list-item>
				</uni-list>
			</view>
			<view style="width: 70%;">
				<uni-card title="服务" :isFull="true" style="border-right: 0 30rpx 0 30rpx;">
					<uni-grid :column="3" :showBorder="false" :highlight="false">
						<uni-grid-item v-for="item in sslist">
							<view style="margin: 20rpx auto;" @click="tose(item.serviceName)">
								<view style="display: flex; margin: auto; width: 100rpx; height: 100rpx; background: #eee;border-radius: 100rpx;">
									<image style="margin: auto; width: 70rpx; height: 70rpx; background: #eee; " :src="gp()+item.imgUrl" mode=""></image>
								</view>
								<view style="width:170rpx; text-align: center;font-weight: bold; margin: auto;">{{item.serviceName}}</view>
							</view>
						</uni-grid-item>
					</uni-grid>
				</uni-card>
			</view>
		</view>
		<u-popup mode="bottom" v-model="show">
			<uni-card title="服务" :isFull="true" style="border-right: 0 30rpx 0 30rpx;">
				<uni-grid :column="5" :showBorder="false" :highlight="false">
					<uni-grid-item v-for="item in ssslist">
						<view style="margin: auto;" @click="tose(item.serviceName)">
							<view style="display: flex; margin: auto; width: 100rpx; height: 100rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 70rpx; height: 70rpx; background: #eee; " :src="gp()+item.imgUrl" mode=""></image>
							</view>
							<view style="width:170rpx; text-align: center;font-weight: bold; margin: auto;">{{item.serviceName}}</view>
						</view>
					</uni-grid-item>
				</uni-grid>
			</uni-card>
		</u-popup>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[{name:'全部服务'},{name:'车主服务'},{name:'便民服务'},{name:'生活服务'}],
				slist:[],
				sslist:[],
				current:0,
				show:false,
				ssslist:[],
				msg:''
			}
		},
		methods: {
			toi(e){
				this.current = e
				if(e==0){
					this.sslist = this.slist
				}else {
					this.sslist = this.slist.filter(res=>{
						return res.serviceType == this.list[e].name
					})
				}
			},
			seart(){
				this.show = true
				this.ssslist = this.slist.filter(res=>{
					return res.serviceName.includes(this.msg)
				})
			},
			tose(e){
				if(e=="门诊预约"){
					uni.navigateTo({
						url: '/pages/service/hospital/hospital',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == "找房子"){
					uni.navigateTo({
						url: '/pages/service/house/house',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == '数据分析'){
					uni.navigateTo({
						url: '/pages/service/yuyuCar/moreXZ/moreXZ',
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
				}else if(e == '停哪儿'){
					uni.navigateTo({
						url: '/pages/service/park/park',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == '外卖订餐'){
					uni.navigateTo({
						url: '/pages/service/movecar/movecar',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == '智慧巴士'){
					uni.navigateTo({
						url: '/pages/service/bus/bus',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == '找工作'){
					uni.navigateTo({
						url: '/pages/service/job/job',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == '看电影'){
					uni.navigateTo({
						url: '/pages/service/traffic/traffic',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e == '生活缴费'){
					uni.navigateTo({
						url: '/pages/service/living/living',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/service/list',
				method: 'GET',
				data: {},
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.slist = res.data.rows
						this.sslist = res.data.rows
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
