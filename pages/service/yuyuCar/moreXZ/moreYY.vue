<template>
	<view>
		<view style="width: 100%; height: 300rpx; background: linear-gradient(180deg,#00dee5,#00eee5); position: absolute;">
			<view style="padding: 20rpx;">
				<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC; background: #fff;">
					<u-form>
						<u-form-item label="预约时间" label-width="150rpx" >
							<uni-datetime-picker type="datetime" v-model="timed"></uni-datetime-picker>
						</u-form-item>
						<u-form-item label="预约地点" label-width="150rpx" >
							<u-input type="text" v-model="city" /><view><u-icon @click="show = true" name="arrow-down"></u-icon></view> 
							<u-picker v-model="show" mode="selector" :range="list" @confirm="get" rangeKey="address"></u-picker>
						</u-form-item>
					</u-form>
				</view>
				<button @click="tot" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#00dee5,#00eee5); color: #fff; margin: 30rpx auto;">确认</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				timed:'',
				show:false,
				list:[],
				city:'',
				id:''
			}
		},
		methods: {
			tot(){
				uni.request({
					url: this.gp()+'/prod-api/api/traffic/checkCar/apply',
					method: 'POST',
					data: {
						"aptTime":this.timed,
						"addressId":this.id
					},
					header:this.th(),
					success: res => {
						console.log(res)
						if(res.data.code == 200){
							uni.navigateBack({
								delta: 1
							});
						}
					},
					fail: () => {},
					complete: () => {}
				});
			},
			get(e){
				this.city = this.list[e].address
				this.id = this.list[e].id
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/traffic/checkCar/place/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.list = res.data.rows
						
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
