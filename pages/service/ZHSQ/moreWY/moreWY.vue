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
				<uni-grid :column="3" :showBorder="false" :highlight="false">
					<uni-grid-item >
						<view @click="tose('物业服务中心')" style="">
							<image style="display: flex; margin: auto; width: 120rpx; height: 120rpx; border-radius: 30rpx; " src="../../../../static/hb/z1.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">物业服务中心</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('停车位服务中心')">
							<image style="display: flex;margin: auto; width: 120rpx; height: 120rpx; border-radius: 30rpx; " src="../../../../static/hb/z3.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">停车位服务中心</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="show = true">
							<image style="display: flex;margin: auto; width: 120rpx; height: 120rpx; border-radius: 30rpx; " src="../../../../static/templateHL.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">24小时值班热线</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="sshow = true">
							<image style="display: flex;margin: auto; width: 120rpx; height: 120rpx; border-radius: 30rpx; " src="../../../../static/templateHL.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">报修电话</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('便民服务')">
							<image style="display: flex;margin: auto; width: 120rpx; height: 120rpx; border-radius: 30rpx; " src="../../../../static/image/zhizao/gy4s.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">便民服务</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('评价反馈')">
							<image style="display: flex;margin: auto; width: 120rpx; height: 120rpx; border-radius: 30rpx; " src="../../../../static/hb/z4.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">评价反馈</view>
						</view>
					</uni-grid-item>
				</uni-grid>
			</view>
			<u-action-sheet :list="slist" @click="click" v-model="show"></u-action-sheet>
			<u-action-sheet :list="sslist" @click="cslick" v-model="sshow"></u-action-sheet>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[{image:'../../../../static/image/banner2.jpg'},{image:'../../../../static/image/banner2.jpg'},{image:'../../../../static/image/banner2.jpg'}],
				show:false,
				sshow:false,
				slist:[{text:'221-12345678'}],
				sslist:[{text:'221-12345678'}]
			}
		},
		methods: {
			tose(e){
				if(e == '物业服务中心'){
					uni.navigateTo({
						url: 'moreWYZX',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="停车位服务中心"){
					uni.navigateTo({
						url: 'moreTCW',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="评价反馈"){
					uni.navigateTo({
						url: 'morePJFK',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="便民服务"){
					uni.navigateTo({
						url: 'moreBM',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}
			},
			click(e){
				uni.makePhoneCall({
					phoneNumber:this.slist[e].text
				})
			},
			cslick(e){
				uni.makePhoneCall({
					phoneNumber:this.sslist[e].text
				})
			}
		}
	}
</script>

<style>

</style>
