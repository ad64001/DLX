<template>
	<view style="padding: 20rpx;">
		<view style="padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC;">
			<u-form>
				<u-form-item label="昵称" label-width="150rpx" >
					<u-input v-model="form.nickName" placeholder="请输入昵称"/>
				</u-form-item>
				<u-form-item label="性别" label-width="150rpx">
					<u-input type="select" v-model="form.sex == 0 ? '男' : '女'" placeholder="请选择性别" @click="show = true"/>
					<u-action-sheet :list="list" @click="cf" v-model="show"></u-action-sheet>
				</u-form-item>
			</u-form>
		</view>
		<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC;">
			<u-form>
				<u-form-item label="身份证号" label-width="150rpx" >
					<u-input v-model="idCard" placeholder="请输入身份证号"/>
				</u-form-item>
				<u-form-item label="手机号" label-width="150rpx" >
					<u-input v-model="form.phonenumber" placeholder="请输入手机号"/>
				</u-form-item>
				<u-form-item label="邮箱" label-width="150rpx" >
					<u-input v-model="form.email" placeholder="请输入邮箱"/>
				</u-form-item>
			</u-form>
		</view>
		<button @click="tl" style="width: 60%; height: 100rpx; background: linear-gradient(90deg,#00d0f0,#00a0f0); color: #fff; margin: 5vh auto;">个人信息修改</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
					show:false,
					list:[{text:'男'},{text:'女'}],
					idCard:'',
					form:{
						nickName:'',
						phonenumber:'',
						sex:'',
						email:'',
						idCard:'',
					}
			}
		},
		methods: {
			cf(e){
				this.form.sex = e
			},
			tl(){
				if(this.idCard.slice(4,14).includes("*")){
					this.idCard = this.idCard.slice(0,4)+this.form.idCard.slice(4,14)+this.idCard.slice(14,18)
					console.log(this.idCard)
				}
				uni.request({
					url: this.gp()+'/prod-api/api/common/user',
					method: 'PUT',
					data: {
						"email": this.form.email,
						"idCard": this.idCard,
						"nickName": this.nickName,
						"phonenumber": this.phonenumber,
						"sex": this.form.sex
					},
					header:this.th(),
					success: res => {
						console.log(res)
						if(res.data.code == 200){
							this.et('修改成功')
							uni.navigateBack()
						}
					},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/common/user/getInfo',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.form = res.data.user
						this.idCard = res.data.user.idCard.slice(0,4) + '*********'+ res.data.user.idCard.slice(14,18)
					}
				},
				fail: () => {},
				complete: () => {}
			});
		}
	}
</script>

<style>
page{
	background: #f9f9f9;
}
</style>
