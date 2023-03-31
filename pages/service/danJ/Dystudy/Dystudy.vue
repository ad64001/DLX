<template>
	<view style="padding: 20rpx;">
		<view>
			<view>
				<u-swiper :list="list"></u-swiper>
			</view>
		</view>
		<view>
			<view style="margin-top: 50rpx;">
				<u-section title="课程分类" lineColor="#F62D59"  :right="false"></u-section>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-grid :column="4" :showBorder="false" :highlight="false">
					<uni-grid-item >
						<view @click="tose()">
							<view style="display: flex; margin: auto; width: 120rpx; height: 120rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 120rpx; height: 120rpx; background: #eee; border-radius: 100rpx; " src="../../../../static/icons/set.png" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">党员行为</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose()">
							<view style="display: flex; margin: auto; width: 120rpx; height: 120rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 120rpx; height: 120rpx; background: #eee; border-radius: 100rpx; " src="../../../../static/icons/add.png" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">中国特色</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose()">
							<view style="display: flex; margin: auto; width: 120rpx; height: 120rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 120rpx; height: 120rpx; background: #eee; border-radius: 100rpx; " src="../../../../static/icons/act.png" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">共产主义</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose()">
							<view style="display: flex; margin: auto; width: 120rpx; height: 120rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 120rpx; height: 120rpx; background: #eee; border-radius: 100rpx; " src="../../../../static/image/zhizao/gy5s.png" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">可持续</view>
						</view>
					</uni-grid-item>
				</uni-grid>
			</view>
		</view>
		<view>
			<view style="margin-top: 50rpx;">
				<u-section title="推荐课程" lineColor="#F62D59"  :right="false"></u-section>
			</view>
			<view style="margin-top: 20rpx;">
				<uni-grid :column="2"  :showBorder="false" :highlight="false">
					<uni-grid-item style="margin-top: 10rpx; margin-bottom: 40rpx;" v-for="(item,index) in 4" >
							<view style="width: 90%;height: 350rpx; box-shadow:0rpx 0rpx 20rpx #eee; border-radius: 40rpx; margin: auto;">
								<navigator style="width: 100%;height: 400rpx;border-radius: 40rpx;">
								<view>
									<image style="width: 100%; height: 200rpx;border-radius: 40rpx; background: #ccc;" src="" mode=""></image>
								</view>
								<view style="padding: 5rpx; word-break: break-all; font-weight: bold;">
									课程示例课程示例课程示例课程示例课程示例课程示例课程示例课程示例
								</view>
								</navigator>
							</view>
					</uni-grid-item>
				</uni-grid>
			</view>
		</view>
		<view>
			<view style="margin-top: 50rpx;">
				<u-section title="推荐书籍" lineColor="#F62D59"  :right="false"></u-section>
			</view>
			<view style="margin-top: 10rpx;">
				<uni-list>
					<uni-list-item v-for="item in 4" to="moreDJH/moreDJH">
						<view slot="header">
							<image style="width: 150rpx; height: 250rpx; background: #ccc; border-radius: 30rpx;" src="" mode=""></image>
						</view>
						<view slot="body" style="margin-left: 20rpx;">
							<view style="font-size: 35rpx; font-weight: bold;word-break: break-all;">习近平强军思想学习问答</view>
							<view style="word-break: break-all;">习近平强军思想学习问答习近平强军思想学习问答习近平强军思想学习问答习近平强军思想学习问答习近平强军思想学习问答习近平强军思想学习问答习近平强军思想学习问答</view>
							<view style="display: flex;margin-top: 10rpx;">
								<view><u-icon name="eye"></u-icon>12</view>
								<view style="margin-left: 20rpx;"><u-icon name="chat"></u-icon>123</view>
								<view style="margin-left: 20rpx;"><u-icon name="thumb-up"></u-icon>123</view>
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
				list:[{image:'../../../../static/image/party/jianghua.jpg'},{image:'../../../../static/image/party/jianghua.jpg'},{image:'../../../../static/image/party/jianghua.jpg'}],
				slist:[{name:'示例'},{name:'示例'},{name:'示例'},{name:'示例'},{name:'示例'}]
			}
		},
		methods: {
			tose(){
				uni.navigateTo({
					url: 'moreKC',
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
