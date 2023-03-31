<template>
	<view>
		<view style="padding: 20rpx; width: 100%; height: 300rpx; border-radius: 0 0 30rpx 30rpx; background: linear-gradient(180deg,#00dee5,#00eee5);">
			<uni-card style="border-radius: 30rpx; margin-top: 20rpx;" :isFull="true">
				<view style="width: 100%; display: flex;">
					<view style="width: 70%; display: inline-block;">
						<u-form>
							<u-form-item label-width="150rpx" label="开始时间" name="">
								<uni-datetime-picker v-model="sti" type="datetime" placeholder="输入开始时间"></uni-datetime-picker>
							</u-form-item>
							<u-form-item label-width="150rpx" label="结束时间" name="">
								<uni-datetime-picker v-model="eti" type="datetime" placeholder="输入结束时间"></uni-datetime-picker>
							</u-form-item>
						</u-form>
						
					</view>
					<view style="width: 25%;margin: auto;">
						<button @click="ches" style="background: linear-gradient(90deg,#00de55,#00ee55); color: #fff; width: 200rpx;">查询</button>
					</view>
				</view>
			</uni-card>
			<view style="margin-top: 20rpx;">
				<view style="margin-top: 50rpx;">
					<u-section title="停车记录" lineColor="#00dee5" :right="false"></u-section>
				</view>
				<view>
					<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC;" v-for="item in sslist.slice(0,index)">
						<u-form>
							<u-form-item label="车牌号" label-width="150rpx" >
								<view>{{item.plateNumber}}/元</view>
							</u-form-item>
							<u-form-item label="停车场名称" label-width="150rpx" >
								<view>{{item.parkName}}</view>
							</u-form-item>
							<u-form-item label="入场时间" label-width="150rpx" >
								<view>{{item.entryTime}}</view>
							</u-form-item>
							<u-form-item label="出场时间" label-width="150rpx" >
								<view>{{item.outTime}}</view>
							</u-form-item>
							<u-form-item label="消费金额" label-width="150rpx" >
								{{item.monetary}}元
							</u-form-item>
						</u-form>
					</view>
				</view>
			</view>
			<view style="margin-top: 20rpx;">
				<button v-show="index < sslist.length - 1" @click="tot" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#00dee5,#00eee5); color: #fff; margin: 30rpx auto;">加载更多</button>
				<u-divider v-show="index > sslist.length - 1">没有更多</u-divider>
			</view>
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				slist:[],
				sslist:[],
				index:5,
				sti:[],
				eti:[]
			}
		},
		methods: {
			che(e){
				
			},
			ches(){
				if(this.sti.length == 0 || this.eti.length == 0 ){
					this.et('请输入时间')
					return
				}else{
					this.sslist = this.slist.filter(res=>{
						if(new Date(this.sti) > new Date(res.entryTime) && new Date(this.eti) < new Date(res.outTime)){
							return true
						}else{
							return false
						}
					})
				}
			},
			tot(){
				this.index += 5
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/park/lot/record/list',
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
page{
	background: #f9f9f9;
}
</style>
