<template>
	<view>
		<view style=" padding: 20rpx; position: absolute; width: 100%; height: 300rpx; background: linear-gradient(180deg,#FFA755,#FF7BA5); border-radius: 0 0 30rpx 30rpx;">
			<view style="padding: 20rpx;">
				<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC; background: #fff;">
					<u-form>
						<u-form-item label="用户账号" label-width="200rpx" >
							<u-input v-model="list.userName"  placeholder="请输入你的姓名"/>
						</u-form-item>
						<u-form-item label="用户昵称" label-width="200rpx" >
							<u-input v-model="list.nickName" placeholder="请输入你的身份证"/>
						</u-form-item>
						<u-form-item label="邮件" label-width="200rpx" >
							<u-input v-model="list.email" placeholder="请输入你的家庭地址"/>
						</u-form-item>
						<u-form-item label="电话号码" label-width="200rpx" >
							<u-input v-model="list.phonenumber" placeholder="请输入你的户口地址"/>
						</u-form-item>
						<u-form-item label="性别" label-width="200rpx" >
							<u-input type="select" v-model="list.sex == 0 ? '男' : '女'" placeholder="请选择性别" @click="show = true"/>
							<u-action-sheet :list="slist" @click="cf" v-model="show"></u-action-sheet>
						</u-form-item>
						<u-form-item  label="现居住地" label-width="200rpx" >
							<u-input v-model="form.address"  placeholder="请输入你的电话号码"/>
						</u-form-item>
						<u-form-item label="教育经历" label-width="200rpx" >
							<u-input v-model="form.education" placeholder="请输入你的电话号码"/>
						</u-form-item>
						<u-form-item label="工作经历" label-width="200rpx" >
							<u-input v-model="form.experience" placeholder="请输入你的电话号码"/>
						</u-form-item>
						<u-form-item label="个人简介" label-width="200rpx" >
							<textarea v-model="form.individualResume" style="width: 100%;"></textarea>
						</u-form-item>
						<u-form-item label="期望薪资" label-width="200rpx" >
							<u-input v-model="form.money" placeholder="请输入你的期望薪资"/>
						</u-form-item>
						<u-form-item label="最高学历" label-width="200rpx" >
							<u-input v-model="form.mostEducation" placeholder="请输入你的最高学历"/>
						</u-form-item>
						<u-form-item label="期望职位" label-width="200rpx" >
							<u-input type="select" v-model="form.positionId" placeholder="请选择职位" @click="sshow = true"/>
							<u-action-sheet :list="sslist" @click="cfs" v-model="sshow"></u-action-sheet>
						</u-form-item>
					</u-form>
				</view>
				<button @click="tl" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#FFA755,#FF7BA5); color: #fff; margin: 30rpx auto;">确认</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:{},
				slist:[{text:"男"},{text:'女'}],
				show:false,
				form:{
					address:'',
					education:'',
					experience:'',
					files:null,
					individualResume:'',
					money:'',
					mostEducation:'',
					positionId:''
				},
				sslist:[],
				sshow:false
			}
		},
		methods: {
			cf(e){
				this.list.sex = this.slist[e].text
			},
			cfs(e){
				this.form.positionId = this.sslist[e].text
			},
			tl(){
				let s = this.sslist.filter(res=>{
					return res.text == this.form.positionId
				})
				console.log(s)
				uni.request({
					url: this.gp()+'/prod-api/api/job/resume',
					method: 'POST',
					data: {
						"mostEducation": this.form.mostEducation,
						"education": this.form.education,
						"address": this.form.address,
						"experience": this.form.experience,
						"individualResume": this.form.individualResume,
						"money": this.form.money,
						"positionId": s.id
					},
					header:this.th(),
					success: res => {
						console.log(res)
						if(res.data.code == 200){
							setTimeout(res=>{
								uni.navigateBack()
							},400)
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
						this.list = res.data.user
					}
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/api/job/profession/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						for(let i of res.data.rows){
							this.sslist.push({
								text:i.professionName,
								id:i.id
							})
						}
						
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
