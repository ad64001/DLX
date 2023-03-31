<template>
	<view>
		<view style="padding: 20rpx; background: linear-gradient(180deg,#F62D59,#FF2D69); width: 100%; height: 300rpx; border-radius:  0 0 20rpx 20rpx; position: absolute;">
			<view style="padding: 20rpx;">
				<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC; background: #fff;">
					<u-form>
						<u-form-item label="路线" label-width="150rpx" >
							<view>{{form.line}}</view>
						</u-form-item>
						<u-form-item label="乘客姓名" label-width="150rpx" >
							<view>{{form.name}}</view>
						</u-form-item>
						<u-form-item label="价格" label-width="150rpx" >
							<view>8元</view>
						</u-form-item>
						<u-form-item label="手机号" label-width="150rpx" >
							<view>{{form.phone}}</view>
						</u-form-item>
						<u-form-item label="上车时间" label-width="150rpx" >
							<view>{{form.time}}</view>
						</u-form-item>
						<u-form-item label="起点" label-width="150rpx" >
							<view>{{form.star}}</view>
							
						</u-form-item>
						<u-form-item label="终点" label-width="150rpx" >
							<view>{{form.end}}</view>
						</u-form-item>
					</u-form>
				</view>
				
			</view>
		</view>
		<button @click="tl"  style="position: fixed; bottom: 0; border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#F62D59,#FF2D69); color: #fff; margin: 30rpx auto;">提交订单</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				form:{
					line:'',
					name:'',
					phone:'',
					star:'',
					end:'',
					time:''
				}
			}
		},
		methods: {
			tl(){
				uni.request({
					url: this.gp()+'/prod-api/api/bus/stop/list',
					method: 'GET',
					data: {
						"start":this.form.star,
						"end":this.form.end,
						"price": 8 ,
						"path":this.form.line,
						"status":1
					},
					success: res => {
						if(res.data.code == 200){
							uni.switchTab({
								url:'/pages/service/user/user'
							})
						}
					},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad() {
			this.form = this.go('bfor')
		}
	}
</script>

<style>

</style>
