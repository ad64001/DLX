<template>
	<view>
		<view>
			<view style="width: 100%; height: 60rpx; background: #0088f0;"></view>
			<uni-nav-bar right-icon="settings" @clickRight="to()" title="登录" backgroundColor="#0088f0" color="#fff"></uni-nav-bar>
		</view>
		<view style="margin-top: 10rpx;">
			<view style="margin-top: 20rpx;">
				<image style="width: 65%; display: flex; margin: auto;" src="../../static/image/logo.png" mode="widthFix"></image>
			</view>
		</view>
		<view style="padding: 20rpx;">
			<u-field icon="account" label="用户名" v-model="user" placeholder="" />
			<u-field icon="lock" password label="密码" v-model="passwd" placeholder="" />
		</view>
		<button @click="tl" style="border-radius: 20rpx; width: 60%; height: 100rpx; background: linear-gradient(90deg,#00d0f0,#00a0f0); color: #fff; margin: 1vh auto;">登录</button>
		<navigator url="register">
			<view style="text-align: center;font-size: 35rpx">注册</view>
		</navigator>
		<view style="display: inline; font-size: 35rpx "><view style="margin-top: 45vh; text-align: center; color: #ccc;">忘记密码</view></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				user:'',
				passwd:''
			}
		},
		methods: {
			to(){
				uni.navigateTo({
					url:'/pages/IPset/IPset'
				})
			},
			csub(e){
				this.current = e
			},
			tl(){
				uni.request({
					url: this.gp()+'/prod-api/api/login',
					method: 'POST',
					data: {
						"username":this.user,
						"password":this.passwd
					},
					success: res => {
						console.log(res)
						this.et(res.data.msg)
						if(res.data.code == 200){
							this.so('user',this.user)
							this.so('passwd',this.passwd)
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
		}
	}
</script>

<style>

</style>
