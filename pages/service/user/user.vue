<template>
	<view>
		<view style=" padding: 20rpx; position: absolute; width: 100%; height: 300rpx; background: linear-gradient(180deg,#0080f0,#0088f0); border-radius: 0 0 100rpx 100rpx;">
			<image style="display: flex; width: 150rpx; height: 150rpx; border-radius: 100rpx; background: #eee; margin: 30rpx auto;" src="../../../static/hb/kele.png" mode=""></image>
			<view style="display: block; color: #fff; text-align: center; font-size: 35rpx; margin-bottom: 20rpx;">你好{{list.nickName}}</view>
		</view>
		<view style="height: 50rpx;">
			
		</view>
		<view style="margin-top: 300rpx;">
			<uni-list>
				<uni-list-item :clickable="true" to="userS/userS" link="navigateTo">
					<view slot="header" style="display: flex; font-size: 35rpx;">
						<u-icon name="account"></u-icon>
						<view style="margin-left: 30rpx;">
							<view>我的信息</view>
						</view>
					</view>
				</uni-list-item>
				<uni-list-item :clickable="true" to="userS/passwd" link="navigateTo">
					<view slot="header" style="display: flex; font-size: 35rpx;">
						<u-icon name="lock"></u-icon>
						<view style="margin-left: 30rpx;">
							<view>修改密码</view>
						</view>
					</view>
				</uni-list-item>
				<uni-list-item :clickable="true" to="userS/order" link="navigateTo">
					<view slot="header" style="display: flex; font-size: 35rpx;">
						<u-icon name="shopping-cart"></u-icon>
						<view style="margin-left: 30rpx;">
							<view>我的订单</view>
						</view>
					</view>
				</uni-list-item>
				<uni-list-item :clickable="true" to="userS/feedback" link="navigateTo">
					<view slot="header" style="display: flex; font-size: 35rpx;">
						<u-icon name="order"></u-icon>
						<view style="margin-left: 30rpx;">
							<view>意见反馈</view>
						</view>
					</view>
				</uni-list-item>
				
			</uni-list>
		</view>
		<button @click="tl" style="border-radius: 20rpx; width: 60%; height: 100rpx; background: linear-gradient(90deg,#00d0f0,#00a0f0); color: #fff; margin: 200rpx auto;">退出登录</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:{}
			}
		},
		methods: {
			tl(){
				uni.navigateTo({
					url: '/pages/login/login',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/common/user/getInfo',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.list = res.data.user
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
