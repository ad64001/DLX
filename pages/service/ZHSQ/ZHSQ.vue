<template>
	<view>
		<view style="padding: 20rpx; background: linear-gradient(180deg,#22c876,#00dee5); width: 100%; height: 300rpx; border-radius:  0 0 20rpx 20rpx; position: absolute;">
			<view>
				<u-search :action-style="{'color':'#fff'}" :input-style="{'background':'#fff'}" bgColor="#fff" borderColor="#fff"/>
			</view>
			<view style="margin-top: 20rpx;">
				<u-swiper :list="list"></u-swiper>
			</view>
			<view style="margin-top: 30rpx;">
				<view style="margin-top: 50rpx; margin-bottom: 20rpx;">
					<u-section title="服务入口" lineColor="#22c876" :right="false" ></u-section>
				</view>
				<uni-grid :column="4" :showBorder="false" :highlight="false">
					<uni-grid-item >
						<view @click="tose('物业服务')" style="">
							<image style="display: flex; margin: auto; width: 120rpx; height: 120rpx; border-radius: 30rpx; " src="../../../static/hb/xianshiqi.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">物业服务</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('快件管理')">
							<image style="display: flex;margin: auto; width: 120rpx; height: 120rpx; border-radius: 30rpx; " src="../../../static/hb/zhixiang.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">快件管理</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('友邻社交')">
							<image style="display: flex;margin: auto; width: 120rpx; height: 120rpx; border-radius: 30rpx; " src="../../../static/image/zhizao/gy6s.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">友邻社交</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('车辆管理')">
							<image style="display: flex;margin: auto; width: 120rpx; height: 120rpx; border-radius: 30rpx; " src="../../../static/image/zhizao/gy3s.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">车辆管理</view>
						</view>
					</uni-grid-item>
				</uni-grid>
			</view>
			<view style="margin-top: 20rpx;">
				<view style="margin-top: 50rpx;">
					<u-section title="社区动态" lineColor="#22c876" :right="false" ></u-section>
				</view>
				<view style="margin-top: 20rpx;">
					<u-subsection active-color="#22c876" :list="slist"></u-subsection>
				</view>
				<view style="margin-top: 10rpx;">
					<uni-list>
						<uni-list-item v-for="item in 4" to="moreTZNR/moreTZNR">
							<view slot="header">
								<image style="border-radius: 20rpx; width: 200rpx; height: 200rpx;" src="../../../static/image/person.jpg" mode=""></image>
							</view>
							<view slot="body" style="margin-left: 20rpx; margin-top: 20rpx;">
								<view style="font-weight: bold;font-size: 35rpx;">物业通知</view>
								<view style="font-weight: bold;">示例动态</view>
								<view>示例动态示例动态示例动态示例动态示例动态示例动态示例动态示例动态示例动态</view>
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
				slist:[{name:'重要通知'},{name:'物业通知'},{name:'社区居委会通知'}]
			}
		},
		methods: {
			tose(e){
				if(e=="物业服务"){
					uni.navigateTo({
						url: 'moreWY/moreWY',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="快件管理"){
					uni.navigateTo({
						url: 'moreKJ/moreKJ',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="友邻社交"){
					uni.navigateTo({
						url: 'moreYLSJ/moreYLSJ',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="车辆管理"){
					uni.navigateTo({
						url: 'moreCL/moreCL',
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

</style>
