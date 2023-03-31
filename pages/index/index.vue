<template>
	<view>
		<swiper style="width: 100%;height: 100vh;" indicator-active-color="#ccc" :indicator-dots="true" :interval="3000" :duration="1000">
			<swiper-item>
				<view class="swiper-item">
					<image style="width: 100%; height: 100vh;" src="" mode=""></image>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item" style="padding: 70rpx 20rpx 0 0; color: #0080f0;">
					<navigator url="../IPset/IPset">
						<view style="text-align: right;">IP设置</view>
					</navigator>
					<button @click="to" style="border-radius: 20rpx; width: 60%; height: 100rpx; background: linear-gradient(90deg,#00d0f0,#00a0f0); color: #fff; margin: 80vh auto;">立即体验</button>
				</view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {
			this.sp('http://124.93.196.45:10001')
			if(this.go('user').length > 0){
				uni.request({
					url: this.gp()+'/prod-api/api/login',
					method: 'POST',
					data: {
						"username":this.go('user'),
						"password":this.go('passwd')
					},
					success: res => {
						console.log(res)
						this.et(res.data.msg)
						if(res.data.code == 200){
							this.so('user',this.go('user'))
							this.so('passwd',this.go('passwd'))
							this.so('token',res.data.token)
							this.et('登陆成功')
							setTimeout(res=>{
								uni.switchTab({
									url:'/pages/home/home'
								})
							},400)
						}
					},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		methods: {
			to(){
				uni.navigateTo({
					url:'/pages/login/login'
				})
			}
		}
	}
</script>

<style>
	
</style>
