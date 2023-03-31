<template>
	<view style="padding: 20rpx;">
		<view style="margin: 2vh auto;">
			<u-field label="IP" v-model="msg" placeholder="192.168.1.1:8080" />
		</view>
		<button @click="tol" style="border-radius: 20rpx; width: 60%; height: 100rpx; background: linear-gradient(90deg,#00d0f0,#00a0f0); color: #fff; margin: 2vh auto;">保存</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				msg:''
			}
		},
		methods: {
			tol(){
				if(this.msg == '' || this.msg == null){
					this.et("请输入ip地址")
					return
				}
				if(this.msg.split('.').length != 4){
					this.et("IP地址有误")
					return
				}else if(this.msg.split(":").length != 2){
					this.et("端口有误")
					return
				}
				this.sp("http://"+this.msg)
				uni.redirectTo({
					url:'/pages/login/login'
				})
			
			}
		}
	}
</script>

<style>

</style>
