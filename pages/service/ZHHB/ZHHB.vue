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
						<view @click="tose('预约历史')" style="">
							<image style="display: flex; margin: auto; width: 120rpx; height: 120rpx; border-radius: 30rpx; " src="../../../static/hb/z3.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">预约历史</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('信息预留')">
							<image style="display: flex;margin: auto; width: 120rpx; height: 120rpx; border-radius: 30rpx; " src="../../../static/hb/z4.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">信息预留</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('附近回收机')">
							<image style="display: flex;margin: auto; width: 120rpx; height: 120rpx; border-radius: 30rpx; " src="../../../static/hb/z2.png" mode=""></image>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">附近回收机</view>
						</view>
					</uni-grid-item>
				</uni-grid>
				<button @click="tl" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#22c876,#00dee5); color: #fff; margin: 10rpx auto;">上门回收</button>
			</view>
			<view style="margin-top: 20rpx;">
				<view style="margin-top: 50rpx;">
					<u-section title="垃圾物品展示" lineColor="#22c876" :right="false" ></u-section>
				</view>
				<view style="margin-top: 50rpx;">
					<u-tabs :list="slist" active-color="#22c876" @change="che" :current="current"></u-tabs>
				</view>
				<view style="margin-top: 10rpx;">
					<uni-list>
						<uni-list-item v-for="item in 4">
							<view slot="header">
								<image style="border-radius: 20rpx; width: 200rpx; height: 200rpx;" src="../../../static/hb/dianchi.png" mode=""></image>
							</view>
							<view slot="body" style="margin-left: 20rpx; margin-top: 20rpx;">
								<view style="font-weight: bold;font-size: 35rpx;">示例名称</view>
								<view style="font-weight: bold;">不可回收</view>
								<view>不可回收不可回收不可回收不可回收不可回收不可回收不可回收不可回收不可回收不可回收不可回收不可回收</view>
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
				slist:[{name:'分类示例'},{name:'分类示例'},{name:'分类示例'},{name:'分类示例'},{name:'分类示例'},{name:'分类示例'},{name:'分类示例'}],
				current:0
			}
		},
		methods: {
			che(e){
				this.current = e
			},
			tose(e){
				if(e=="信息预留"){
					uni.navigateTo({
						url: '/pages/service/ZHHB/moreYL/moreYL',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="预约历史"){
					uni.navigateTo({
						url: '/pages/service/ZHHB/moreHBL/moreHBL',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="附近回收机"){
					uni.navigateTo({
						url: '/pages/service/ZHHB/moreFHS/moreFHS',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}
			},
			tl(){
				uni.navigateTo({
					url: '/pages/service/ZHHB/moreZL/moreZL',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		}
	}
</script>

<style>

</style>
