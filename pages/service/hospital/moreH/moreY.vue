<template>
	<view style="padding: 20rpx;">
		<view>
			<uni-card style="border-radius: 30rpx; border: 1rpx solid #ccc; margin-top: 20rpx;" :isFull="true" v-for="item in list">
				<view style="width: 100%; display: flex;">
					<view style="width: 25%;"  @click="add(item.id)">
						<image v-show="item.imgUrl == null" style="width: 100%; height: 280rpx; background: #eee;" src="" mode=""></image>
					</view>
					<view style="width: 65%; margin-left: 20rpx; font-size: 25rpx;font-weight: bold;">
						<view style="text-align: right; position: absolute;right: 2vw; font-size: 35rpx;"><u-icon @click="toG(item.id)" name="arrow-right-double"></u-icon></view>
						<view style="">姓名:{{item.name}}</view>
						<view style="margin-top: 25rpx;">身份证:{{item.cardId}}</view>
						<view style="margin-top: 25rpx;">性别:{{item.sex == 0 ?  '男' : '女'}}</view>
						<view style="margin-top: 25rpx;">电话:{{item.tel}}</view>
						<view style="margin-top: 25rpx;">出生日期:{{item.birthday}}</view>
					</view>
				</view>
			</uni-card>
		</view>
		<view style="margin-top: 20rpx;">
			<button @click="add(0)" style="width: 100%;background: linear-gradient(90deg,#22c786,#10aebe);color: #fff;">+</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[],
				slist:[]
			}
		},
		methods: {
			add(e){
				uni.navigateTo({
					url: 'moreA?id='+e,
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			},
			toG(e){
				this.slist = this.list.filter(res=>{
					return res.id = e
				})
				this.so('hoe',this.slist)
				uni.navigateTo({
					url: 'moreG',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/hospital/patient/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.list = res.data.rows
					}
				},
				fail: () => {},
				complete: () => {}
			});
		}
	}
</script>

<style>

</style>
