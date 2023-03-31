<template>
	<view>
		<view style="width: 100%; position: fixed; z-index: 99;">
			<u-subsection active-color="#22c786" :list="list" :current="current" @change="che"></u-subsection>
		</view>
		<view style="height: 15rpx;"></view>
		<view  style="padding: 20rpx;">
			<view v-show="current == 0" style="margin-top: 70rpx;">
				<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC;">
					<u-form>
						<u-form-item label="科室分类" label-width="150rpx" >
							<view>{{form.category}}</view>
						</u-form-item>
						<u-form-item label="金额" label-width="150rpx" >
							<view>{{form.money}}/元</view>
						</u-form-item>
						<u-form-item label="患者姓名" label-width="150rpx" >
							<view>{{form.patientName}}</view>
						</u-form-item>
						<u-form-item label="预约时间" label-width="150rpx" >
							<uni-datetime-picker type="datetime" v-model="form.reserveTime" placeholder="预约时间"></uni-datetime-picker>
						</u-form-item>
						<u-form-item label="门诊类型" label-width="150rpx" >
							<view>{{form.type == 1 ? '普通号' : '专家号'}}</view>
						</u-form-item>
					</u-form>
				</view>
			</view>
			<button v-show="current == 0" @click="tl" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#22c786,#10aebe); color: #fff; margin: 30rpx auto;">确认</button>
			<view v-show="current == 1" style="margin-top: 40vh;">
				<u-divider>暂无数据</u-divider>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[{name:'普通号'},{name:'专家号'}],
				current:0,
				slist:[],
				form:{
					category:'',
					categoryId:'',
					money:'5',
					patientName:'',
					reserveTime:'',
					type:''
				}
			}
		},
		methods: {
			che(e){
				this.current = e
			},
			tl(){
				uni.request({
					url: this.gp()+'/prod-api/api/hospital/patient',
					method: 'POST',
					data: {
						"categoryId": this.form.categoryId,
						"money": this.form.money,
						"patientName": this.form.patientName,
						"reserveTime": this.form.reserveTime,
						"type": this.form.type
					},
					header:this.th(),
					success: res => {
						console.log(res)
						if(res.data.code == 200){
							setTimeout(res=>{
								uni.navigateTo({
									url:'moreL'
								});
							},400)
							
						}
					},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad(e) {
			this.form.categoryId = e.ir
			this.form.category = e.id
			this.slist = this.go('hoe')
			this.form.patientName = this.slist[0].name
			this.form.type = this.current + 1
		}
	}
</script>

<style>

</style>
