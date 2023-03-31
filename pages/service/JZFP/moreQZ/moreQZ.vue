<template>
	<view style="padding: 20rpx;">
		<view>
			<u-subsection active-color="#F62D59" :list="list" @change="che" :current="current"></u-subsection>
		</view>
		<view style="margin-top: 20rpx;">
			<u-section title="求助列表" lineColor="#F62D59"  :right="false"></u-section>
		</view>
		<view v-show="current == 0">
			<uni-card style="border: 1rpx solid #ccc; border-radius: 30rpx; margin-top: 20rpx;" :isFull="true" v-for="(item,index) in 4">
				<view style="width: 100%; display: flex;">
					<view style="width: 10%;">
						<image style="margin: auto; display: flex; width: 50rpx; height: 50rpx;" src="../../../../static/icons/user_act.png" mode=""></image>
					</view>
					<view style="width: 65%; margin: auto; color: #666666;">
						发布人
					</view>
				</view>
				<u-line margin="10rpx"></u-line>
				<view style="width: 100%; height: 250rpx; display: flex;" >
					<view style="width: 25%;height: 100%;">
						<image style="width: 150rpx; height: 150rpx; display: flex; margin: 40rpx auto; justify-content: center; align-items: center;" src="../../../../static/hb/dianchi.png" mode=""></image>
					</view>
					<view style="width: 75%;">
						<view style="text-align: right; color: #ccc;">已解决</view>
						<view style=" margin-top: 20rpx; color: #666666;">解决时间:1919-4-16 10:24:36</view>
						<view style="font-size: 35rpx; color: orangered; margin-top: 20rpx;display: flex;">解决人:示例</view>
						<view style="font-size: 35rpx; color: #666666; margin-top: 20rpx;">需求</view>
						<view></view>
					</view>
				</view>
			</uni-card>
		</view>
		<view v-show="current == 1">
			<uni-card style="border: 1rpx solid #ccc; border-radius: 30rpx; margin-top: 20rpx;" :isFull="true" v-for="(item,index) in 4">
				<view style="width: 100%; display: flex;">
					<view style="width: 10%;">
						<image style="margin: auto; display: flex; width: 50rpx; height: 50rpx;" src="../../../../static/icons/user_act.png" mode=""></image>
					</view>
					<view style="width: 65%; margin: auto; color: #666666;">
						发布人
					</view>
				</view>
				<u-line margin="10rpx"></u-line>
				<view style="width: 100%; height: 250rpx; display: flex;" >
					<view style="width: 25%;height: 100%;">
						<image style="width: 150rpx; height: 150rpx; display: flex; margin: 40rpx auto; justify-content: center; align-items: center;" src="../../../../static/hb/dianchi.png" mode=""></image>
					</view>
					<view style="width: 75%;">
						<view style="text-align: right; color: #ccc;">未解决</view>
						<view style=" margin-top: 20rpx; color: #666666;">发布时间:1919-4-16 10:24:36</view>
						<view style="font-size: 35rpx; color: orangered; margin-top: 20rpx;display: flex;">解决人:</view>
						<view style="font-size: 35rpx; color: #666666; margin-top: 20rpx; margin-bottom: 20rpx;">需求</view>
						<view><button style="position: absolute; right: 20rpx; bottom: 10rpx; margin-top: 20rpx; margin-bottom: 10rpx; color: #fff; background: #F62D59; font-size: 20rpx; width: 200rpx;">去解决</button></view>
					</view>
				</view>
			</uni-card>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[{name:'已解决'},{name:'未解决'}],
				current:0
			}
		},
		methods: {
			che(e){
				this.current  = e
			}
		}
	}
</script>

<style>

</style>
