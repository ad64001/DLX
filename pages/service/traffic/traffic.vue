<template>
	<view>
		<view style="padding: 20rpx; width: 100%; height: 300rpx; background: linear-gradient(180deg,#00dee5,#00eee5); border-radius: 0 0 30rpx 30rpx;">
			<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC; background: #fff;">
				<u-form>
					<u-form-item label="车牌地区" label-width="150rpx" >
						<u-input   placeholder="请输入你的号牌种类 如'京'"/>
					</u-form-item>
					<u-form-item label="车牌号码" label-width="150rpx" >
						<u-input  placeholder="请输入车牌号 如A88888"/>
					</u-form-item>
					<u-form-item label="号牌种类" label-width="150rpx" >
						<u-input  placeholder="请输入你的号牌种类"/>
					</u-form-item>
					<u-form-item label="发动机号" label-width="150rpx" >
						<u-input  placeholder="请输入你的发动机号"/>
					</u-form-item>
				</u-form>
			</view>
			<button @click="tl" style="border-radius: 20rpx; width: 60%; height: 100rpx; background: linear-gradient(90deg,#00dee5,#00eee5); color: #fff; margin: 200rpx auto;">查询违章</button>
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
				uni.navigateTo({
					url: 'moreTCX/moreTCX',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		}
	}
</script>

<style>
page{
	background: #f9f9f9;
}
</style>
