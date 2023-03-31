<template>
	<view>
		<view style="margin-top: 30rpx; padding: 20rpx;">
			<view>
				<u-section title="违章详情" lineColor="#00dee5" :right="false"></u-section>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-list style="border-radius: 30rpx;">
					<uni-list-item style="background: #f9f9f9;">
						<view slot="header">
							<view>违章地点:示例北京二环高速路</view>
						</view>
					</uni-list-item>
					
					<uni-list-item>
						<view slot="header">
							<view>处罚日期:示例1919-12-14 10:23:46</view>
						</view>
					</uni-list-item>
					<uni-list-item style="background: #f9f9f9;">
						<view slot="header">
							<view>处罚单位:示例北京交警大队</view>
						</view>
					</uni-list-item>
					<uni-list-item>
						<view slot="header">
							<view>违章行为:乱停车示例</view>
						</view>
					</uni-list-item>
					<uni-list-item style="background: #f9f9f9;">
						<view slot="header">
							<view>金额:99999元</view>
						</view>
					</uni-list-item>
					<uni-list-item>
						<view slot="header">
							<view>通知书号:1145141919</view>
						</view>
					</uni-list-item>
				</uni-list>
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
			
		}
	}
</script>

<style>

</style>
