<template>
	<view>
		<view style=" width: 100%; height: 300rpx; background: linear-gradient(180deg,#00d0f0,#00a0f0); position: absolute; border-radius: 0 0 30rpx 30rpx;">
			
			<view style="padding: 20rpx;">
				<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC; background: #fff;">
					<u-form>
						<u-form-item label="你要添加的户号" label-width="250rpx" >
							<u-input  placeholder="请输入户号"/>
						</u-form-item>
						<u-form-item label="添加的人" label-width="250rpx" >
							<u-input  placeholder="请输入要添加的人"/>
						</u-form-item>
					</u-form>
				</view>
				<button @click="tl" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#00d0f0,#00a0f0); color: #fff; margin: 70rpx auto;">确认</button>
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
				this.et('添加成功')
				setTimeout(res=>{
					uni.navigateBack({
						delta: 1
					},400);
				})
			}
		}
	}
</script>

<style>

</style>
