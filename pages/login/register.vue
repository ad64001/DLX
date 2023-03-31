<template>
	<view>
		<view style="padding: 30rpx;">
			<u-form>
				<u-form-item label="用户名" label-width="150rpx">
					<u-input v-model="form.userName" placeholder="请输入用户名"/>
				</u-form-item>
				<u-form-item label="昵称" label-width="150rpx" >
					<u-input v-model="form.nickName" placeholder="请输入昵称"/>
				</u-form-item>
				<u-form-item label="性别" label-width="150rpx">
					<u-input type="select" v-model="form.sex == 0 ? '男' : '女'" placeholder="请选择性别" @click="show = true"/>
					<u-action-sheet :list="list" @click="cf" v-model="show"></u-action-sheet>
				</u-form-item>
			</u-form>
		</view>
		
		<view style="width: 100%;height: 20rpx; background: #eee;"></view>
		
		<view style="padding: 30rpx;">
			<u-form>
				<u-form-item label="邮箱" label-width="150rpx">
					<u-input v-model="form.email" placeholder="请输入邮箱"/>
				</u-form-item>
				<u-form-item label="身份证" label-width="150rpx">
					<u-input v-model="form.idCard" placeholder="请输入身份证"/>
				</u-form-item>
				<u-form-item label="电话号码" label-width="150rpx">
					<u-input v-model="form.phonenumber" placeholder="请输入电话号码"/>
				</u-form-item>
			</u-form>
		</view>
		
		<view style="width: 100%;height: 20rpx; background: #eee;"></view>
		<view style="padding: 30rpx;">
			<u-form>
				<u-form-item label="密码" label-width="150rpx">
					<u-input password v-model="form.password" placeholder="请输入密码"/>
				</u-form-item>
			</u-form>
		</view>
		<view style="width: 100%;height: 20rpx; background: #eee;"></view>
		<button @click="to" style="border-radius: 20rpx; width: 60%; height: 100rpx; background: linear-gradient(90deg,#00d0f0,#00a0f0); color: #fff; margin: 1vh auto;">注册</button>
	</view>
	
</template>

<script>
	export default {
		data() {
			return {
				form:{
					userName:'',
					nickName:'',
					password:'',
					phonenumber:'',
					sex:'',
					email:'',
					idCard:'',
				},
				show:false,
				list:[{text:'男'},{text:'女'}]
			}
		},
		methods: {
			cf(e){
				this.form.sex = e
			},
			to(){
				if(this.form.userName == ""||
				this.form.nickName == ""||
				this.form.password == ""||
				this.form.phonenumber == ""||
				this.form.email == ""||
				this.form.idCard == ""){
					this.et('请输入完整')
					return
				}
				if(this.form.phonenumber.length != 11 ){
					this.et('电话号码有误')
					return
				}else if(this.form.idCard.length != 18){
					this.et('身份证输入有误')
					return
				}
				uni.request({
					url: this.gp()+'/prod-api/api/register',
					method: 'POST',
					data: {
						"userName": this.form.userName ,
						"nickName": this.form.nickName,
						"password": this.form.password,
						"phonenumber":this.form.phonenumber,
						"sex": this.form.sex,
						"email": this.form.email,
						"idCard": this.form.idCard
					},
					success: res => {
						console.log(res)
						this.et(res.data.msg)
						if(res.data.code == 200){
							this.et('注册成功')
							setTimeout(res=>{
								uni.navigateBack()
							},400)
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
