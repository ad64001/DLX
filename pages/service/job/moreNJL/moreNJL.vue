<template>
	<view style="padding: 20rpx;">
		<view style="padding: 20rpx;">
			<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC; background: #fff;">
				<u-form>
					<u-form-item  label="现居住地" label-width="200rpx" >
						<view v-if="list.address">{{list.address}}</view>
					</u-form-item>
					<u-form-item label="教育经历" label-width="200rpx" >
						<view>{{list.education}}</view>
					</u-form-item>
					<u-form-item label="工作经历" label-width="200rpx" >
						<view>{{list.experience}}</view>
					</u-form-item>
					<u-form-item label="个人简介" label-width="200rpx" >
						<textarea v-model="list.individualResume" style="width: 100%;"></textarea>
					</u-form-item>
					<u-form-item label="期望薪资" label-width="200rpx" >
						<view>{{list.money}}</view>
					</u-form-item>
					<u-form-item label="最高学历" label-width="200rpx" >
						<view>{{list.mostEducation}}</view>
					</u-form-item>
				</u-form>
			</view>
		</view>
		<button @click="tl" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#FFA755,#FF7BA5); color: #fff; margin: 200rpx auto;">修改学历</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id:'',
				list:{},
				po:''
			}
		},
		methods: {
			tl(){
				uni.navigateTo({
					url: '/pages/service/job/moreNJL/moreAJL?id='+this.id,
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad(e) {
			this.id = e.id
			uni.request({
				url: this.gp()+'/prod-api/api/job/resume/queryResumeByUserId/'+e.id,
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.list = res.data.data
						uni.request({
							url: this.gp()+'/prod-api/api/job/profession/list',
							method: 'GET',
							data: {},
							header:this.th(),
							success: res1 => {
								console.log(res1)
								if(res1.data.code == 200){
									this.po = res1.data.rows.filter(res2=>{
									return res2.id == res.data.data.positionId
									})
								}
							},
							fail: () => {},
							complete: () => {}
						});
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
