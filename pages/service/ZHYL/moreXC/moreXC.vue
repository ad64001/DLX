<template>
	<view  style="padding: 20rpx;">
		<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC;" v-for="(item,index) in 4">
			<u-form>
				<u-form-item label="餐饮服务" label-width="150rpx" >
					<view>已经完成</view>
				</u-form-item>
				<u-form-item label="餐饮时间" label-width="150rpx" >
					<view>10:58:11</view>
				</u-form-item>
				<u-form-item label="人员评价" label-width="150rpx" >
					<view>示例示例示例示例示例示例示例示例</view>
				</u-form-item>
			</u-form>
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
			
		}
	}
</script>

<style>

</style>
