<template>
	<view>
		<view style=" width: 100%; height: 400rpx; background: linear-gradient(180deg,#22c876,#00dee5); position: absolute; border-radius: 0 0 30rpx 30rpx;">
			
			<view style="padding: 20rpx;">
				<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC; background: #fff;">
					<u-form>
						<u-form-item label="时间" label-width="150rpx" >
							<uni-datetime-picker type="datetime" placeholder="具体时间"></uni-datetime-picker>
						</u-form-item>
						<u-form-item label="姓名" label-width="150rpx" >
							<u-input  placeholder="请输入你的姓名"/>
						</u-form-item>
						<u-form-item label="手机号" label-width="150rpx" >
							<u-input  placeholder="请输入你的手机号"/>
						</u-form-item>
						<u-form-item label="家庭地址" label-width="150rpx" >
							<u-input  placeholder="请输入你的家庭地址"/>
						</u-form-item>
						<u-form-item label="垃圾图片" label-width="150rpx" >
							
						</u-form-item>
					</u-form>
					<uni-file-picker limit="9"></uni-file-picker>
				</view>
				<button @click="tl" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#22c876,#00dee5); color: #fff; margin: 30rpx auto;">确认</button>
			</view>
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			tl(){
				uni.navigateBack({
					delta: 1
				});
			}
		}
	}
</script>

<style>

</style>
