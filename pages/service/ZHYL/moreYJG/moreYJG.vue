<template>
	<view style="padding: 20rpx;">
		<view>
			<view style="margin-top: 20rpx;">
				<u-section title="养老机构列表" lineColor="#0080f0" :right="false" ></u-section>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-list>
					<uni-list-item v-for="item in 9" to="moreYLYJJ">
						<view slot="header">
							<image style="border-radius: 20rpx; width: 300rpx; height: 200rpx; background: #ccc;" src="" mode=""></image>
						</view>
						<view slot="body" style="margin-left: 20rpx;">
							<view style="font-size: 35rpx; font-weight: bold;word-break: break-all;">养老院</view>
							<view style="display: flex;">三零三零六十六三零三零六十六三零三零六十六</view>
							<view style="margin-top: 2vh;">
								<u-rate :current="4"></u-rate>
							</view>
							
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
