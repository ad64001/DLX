<template>
	<view style="padding: 20rpx;">
		<view style="padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC;">
			<u-form>
				<u-form-item label="姓名" label-width="150rpx" >
					<u-input v-model="form.name" placeholder="请输入昵称"/>
				</u-form-item>
				<u-form-item label="性别" label-width="150rpx">
					<u-input type="select" v-model="form.sex == 0 ? '男' : '女'" placeholder="请选择性别" @click="show = true"/>
					<u-action-sheet :list="list" @click="cf" v-model="show"></u-action-sheet>
				</u-form-item>
			</u-form>
		</view>
		<view style="padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC; margin-top: 20rpx;">
			<u-form>
				<u-form-item label="电话" label-width="150rpx" >
					<u-input v-model="form.tel" placeholder="请输入电话号码"/>
				</u-form-item>
				<u-form-item label="身份证" label-width="150rpx" >
					<u-input v-model="form.cardId" placeholder="请输入身份证"/>
				</u-form-item>
				<u-form-item label="家庭住址" label-width="150rpx" >
					<u-input v-model="form.address" placeholder="请输入家庭住址"/>
				</u-form-item>
				<u-form-item label="出生年月日" label-width="150rpx" >
					<uni-datetime-picker type="date" v-model="form.birthday"></uni-datetime-picker>
				</u-form-item>
			</u-form>
		</view>
		<button @click="tl" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#22c786,#10aebe); color: #fff; margin: 30rpx auto;">确认</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				show:false,
				list:[{text:'男'},{text:'女'}],
				form:{
					name:'',
					tel:'',
					sex:'',
					birthday:'',
					cardId:'',
					address:''
				},
				id:0,
				slist:[]
			}
		},
		methods: {
			cf(e){
				this.form.sex = e
			},
			tl(){
				if(this.id == 0){
					uni.request({
						url: this.gp()+'/prod-api/api/hospital/patient',
						method: 'POST',
						data: {
							"address": this.form.address,
							"birthday": this.form.birthday,
							"cardId": this.form.cardId,
							"name": this.form.name,
							"sex": this.form.sex,
							"tel": this.form.tel
						},
						header:this.th(),
						success: res => {
							console.log(res)
							if(res.data.code == 200){
								uni.navigateTo({
									url:'/pages/service/hospital/moreH/moreY'
								});
							}
						},
						fail: () => {},
						complete: () => {}
					});
				}else {
					uni.request({
						url: this.gp()+'/prod-api/api/hospital/patient',
						method: 'PUT',
						data: {
							"id":this.id,
							"address": this.form.address,
							"birthday": this.form.birthday,
							"cardId": this.form.cardId,
							"name": this.form.name,
							"sex": this.form.sex,
							"tel": this.form.tel
						},
						header:this.th(),
						success: res => {
							console.log(res)
							if(res.data.code == 200){
								uni.navigateBack();
							}
						},
						fail: () => {},
						complete: () => {}
					});
				}
			}
		},
		onLoad(e) {
			this.id = e.id
			if(e.id != 0){
				uni.request({
					url: this.gp()+'/prod-api/api/hospital/patient/list',
					method: 'GET',
					data: {},
					header:this.th(),
					success: res => {
						console.log(res)
						if(res.data.code == 200){
							this.slist = res.data.rows.filter(res=>{
								return res.id = e.id
							})
							this.form = this.slist[0]
						}
					},
					fail: () => {},
					complete: () => {}
				});
			}
		}
	}
</script>

<style>

</style>
