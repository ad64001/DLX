<template>
	<view style="padding: 20rpx;">
		<view>
			<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC;" v-for="item in slist">
				<u-form>
					<u-form-item label="患者姓名" label-width="150rpx" >
						<view>{{item.patientName}}</view>
					</u-form-item>
					<u-form-item label="金额" label-width="150rpx" >
						<view>{{item.money}}/元</view>
					</u-form-item>
					<u-form-item label="科室类别" label-width="150rpx" >
						<view>{{item.categoryName}}</view>
					</u-form-item>
					<u-form-item label="预约时间" label-width="150rpx" >
						<view>{{item.reserveTime}}</view>
					</u-form-item>
					<u-form-item label="预约单号" label-width="150rpx" >
						{{item.orderNo}}
					</u-form-item>
					<u-form-item label="门诊类型" label-width="150rpx" >
						<view>{{item.type == 1 ? '普通号' : '专家号'}}</view>
					</u-form-item>
				</u-form>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				slist:[]
			}
		},
		methods: {
			
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/hospital/reservation/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.slist = res.data.rows
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
