<template>
	<view style="padding: 20rpx;">
		<view style="padding: 50rpx;">
			<u-form>
				<u-form-item label="旧密码" label-width="150rpx">
					<u-input type="password"  v-model="opassword" placeholder="请输入旧密码"/>
				</u-form-item>
				<u-form-item label="新密码" label-width="150rpx">
					<u-input type="password" v-model="npassword" placeholder="请输入新密码"/>
				</u-form-item>
			</u-form>
			<button @click="tl" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#00d0f0,#00a0f0); color: #fff; margin: 30rpx auto;">确认</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				opassword:'',
				npassword:''
			}
		},
		methods: {
			tl(){
				if(this.opassword == '' || this.npassword == ''){
					this.et('新/旧密码不能为空')
					return
				}
				uni.request({
					url: this.gp()+'/prod-api/api/common/user/resetPwd',
					method: 'PUT',
					data: {
						"newPassword": this.npassword,
						"oldPassword": this.opassword
					},
					header:this.th(),
					success: res => {
						this.et(res.data.msg)
						console.log(res)
						if(res.data.code == 200){
							uni.navigateBack();
						}
					},
					fail: () => {},
					complete: () => {}
				});
			}
		}
	}
</script>

<style>

</style>
