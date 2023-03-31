<template>
	<view>
		<view style="padding: 20rpx; background: linear-gradient(180deg,#F62D59,#FF2D69); width: 100%; height: 300rpx; border-radius:  0 0 20rpx 20rpx; position: absolute;">
			<view>
				<u-search :action-style="{'color':'#fff'}" :input-style="{'background':'#fff'}" bgColor="#fff" borderColor="#fff"/>
			</view>
			<view style="margin-top: 20rpx;">
				<u-swiper :list="list"></u-swiper>
			</view>
		</view>
		<view style="height:15rpx;"></view>
		<view style="margin-top: 350rpx; padding: 20rpx;">
			<view>
				<uni-grid :column="4" :showBorder="false" :highlight="false">
					<uni-grid-item >
						<view @click="tose('党员学习')">
							<view style="display: flex; margin: auto; width: 120rpx; height: 120rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 120rpx; height: 120rpx; background: #eee; border-radius: 100rpx; " src="../../../static/image/zhizao/gy3s.png" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">党员学习</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('组织活动')">
							<view style="display: flex; margin: auto; width: 120rpx; height: 120rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 120rpx; height: 120rpx; background: #eee; border-radius: 100rpx; " src="../../../static/icons/act.png" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">组织活动</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('建言献策')">
							<view style="display: flex; margin: auto; width: 120rpx; height: 120rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 120rpx; height: 120rpx; background: #eee; border-radius: 100rpx; " src="../../../static/icons/party.jpg" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">建言献策</view>
						</view>
					</uni-grid-item>
					<uni-grid-item >
						<view @click="tose('随手拍')">
							<view style="display: flex; margin: auto; width: 120rpx; height: 120rpx; background: #eee;border-radius: 100rpx;">
								<image style="margin: auto; width: 120rpx; height: 120rpx; background: #eee; border-radius: 100rpx; " src="../../../static/image/zhizao/gy5s.png" mode=""></image>
							</view>
							<view style="width:150rpx; text-align: center;font-weight: bold;margin: 15rpx auto;">随手拍</view>
						</view>
					</uni-grid-item>
				</uni-grid>
			</view>
			<view>
				<view style="margin-top: 50rpx;">
					<u-section title="党建动态" lineColor="#F62D59"  @click="tose('党建动态')"></u-section>
				</view>
				
				<view style="margin-top: 20rpx;">
					<scroll-view scroll-x="true" style="white-space: nowrap; width: 100%;">
						<view style="display: flex;">
							<view style="margin-left: 30rpx; width: 750rpx; border-radius: 30rpx; border: 1rpx solid #ccc; padding: 10rpx;" v-for="item in 4">
								<navigator style="display: flex;">
									<view style="width: 40%;">
										<image style="border-radius: 20rpx; width: 300rpx; height: 200rpx;" src="../../../static/image/studyImg.png" mode=""></image>
									</view>
									<view  style="width: 55%; margin-left: 60rpx;">
										<view style="display: inline; font-size: 35rpx; font-weight: bold; word-break: break-all;">例示例示例例</view>
										<view>例示例示例例例示例示</view>
										<view style="display: flex;margin-top: 40rpx;">
											<view><u-icon name="eye"></u-icon>12</view>
											<view style="margin-left: 20rpx;"><u-icon name="chat"></u-icon>12</view>
											<view style="margin-left: 20rpx;"><u-icon name="thumb-up"></u-icon>12</view>
										</view>
										
										<view style="margin-top: 10rpx;">发布时间:114514-19-19</view>
									</view>
								</navigator>
							</view>
						</view>
					</scroll-view>
				</view>
			</view>
			<view style="margin-top: 20rpx;">
				<view style="margin-top: 20rpx;">
					<u-subsection active-color="#F62D59" :list="slist"></u-subsection>
				</view>
				<view style="margin-top: 10rpx;">
					<uni-list>
						<uni-list-item v-for="item in 4" to="moreDJH/moreDJH">
							<view slot="header">
								<view style="font-size: 35rpx; font-weight: bold;word-break: break-all;">蘑菇屋是一款,用户可以定制合租室友，发布合租需求，还提供了众多生活服务，认识身边志趣相投的朋友</view>
								<view style="display: flex;margin-top: 10rpx;">
									<view><u-icon name="eye"></u-icon>12</view>
									<view style="margin-left: 20rpx;"><u-icon name="chat"></u-icon>123</view>
									<view style="margin-left: 20rpx;"><u-icon name="thumb-up"></u-icon>123</view>
								</view>
								
								<view style="margin-top: 10rpx;">发布时间:1919-12-15</view>
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
				list:[{image:'../../../static/image/party/jianghua.jpg'},{image:'../../../static/image/party/jianghua.jpg'},{image:'../../../static/image/party/jianghua.jpg'}],
				slist:[{name:'共产党'},{name:'热点新闻'},{name:'扶贫成果'}]
			}
		},
		methods: {
			tose(e){
				if(e=="党员学习"){
					uni.navigateTo({
						url: '/pages/service/danJ/Dystudy/Dystudy',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="组织活动"){
					uni.navigateTo({
						url: 'moreHD/moreHD',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="建言献策"){
					uni.navigateTo({
						url: 'moreJY/moreJY',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else if(e=="随手拍"){
					uni.navigateTo({
						url: "moreSSP/moreSSP",
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
				}else{
					uni.navigateTo({
						url: "moreDT/moreDT",
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
