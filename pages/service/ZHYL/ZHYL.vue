<template>
	<view>
		<view style="padding: 20rpx; background: linear-gradient(180deg,#0080f0,#0088f0); width: 100%; height: 300rpx; border-radius:  0 0 20rpx 20rpx; position: absolute;">
			<view>
				<u-search :action-style="{'color':'#fff'}" :input-style="{'background':'#fff'}" bgColor="#fff" borderColor="#fff"/>
			</view>
			<view style="margin-top: 20rpx;">
				<u-swiper :list="list"></u-swiper>
			</view>
			<view style="margin-top: 30rpx;">
				<view style="margin-top: 50rpx; margin-bottom: 20rpx;">
					<u-section title="服务入口" lineColor="#0080f0" :right="false" ></u-section>
				</view>
				<uni-grid :column="4" :showBorder="false" :highlight="false">
					<uni-grid-item >
						<view @click="tose('养老机构')" style="">
							<image style="display: flex; margin: auto; width: 100rpx; height: 100rpx; border-radius: 30rpx; " src="../../../static/icons/act.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">养老机构</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('入住房间')">
							<image style="display: flex;margin: auto; width: 100rpx; height: 100rpx; border-radius: 30rpx; " src="../../../static/hb/z1.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">入住房间</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('服务巡检')">
							<image style="display: flex;margin: auto; width: 100rpx; height: 100rpx; border-radius: 30rpx; " src="../../../static/hb/z4.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">服务巡检</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('健康评估')">
							<image style="display: flex;margin: auto; width: 100rpx; height: 100rpx; border-radius: 30rpx; " src="../../../static/icons/all_act.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">健康评估</view>
						</view>
					</uni-grid-item>
				</uni-grid>
			</view>
			<view style="margin-top: 20rpx;">
				<view style="margin-top: 20rpx;">
					<u-section title="养老机构推荐" lineColor="#0080f0" :right="false" ></u-section>
				</view>
				<view style="margin-top: 20rpx;">
					<uni-list>
						<uni-list-item v-for="item in 4" to="moreYJG/moreYLYJJ">
							<view slot="header">
								<image style="border-radius: 20rpx; width: 300rpx; height: 200rpx; background: #ccc;" src="" mode=""></image>
							</view>
							<view slot="body" style="margin-left: 20rpx;">
								<view style="font-size: 35rpx; font-weight: bold;word-break: break-all;">模范养老院</view>
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
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[{image:'../../../static/image/banner2.jpg'},{image:'../../../static/image/banner2.jpg'},{image:'../../../static/image/banner2.jpg'}],
			}
		},
		methods: {
			tose(e){
				if(e=="养老机构"){
					uni.navigateTo({
						url: '/pages/service/ZHYL/moreYJG/moreYJG',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="入住房间"){
					uni.navigateTo({
						url: '/pages/service/ZHYL/moreRZ/moreRZ',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="服务巡检"){
					uni.navigateTo({
						url: 'moreXC/moreXC',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="健康评估"){
					uni.navigateTo({
						url: 'morePG/morePG',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}
			}
		}
	}
</script>

<style>
page{
	background: #f9f9f9;
}
</style>
