<template>
	<view>
		<view style="padding: 20rpx; background: linear-gradient(180deg,#F62D59,#FF2D69); width: 100%; height: 300rpx; border-radius:  0 0 20rpx 20rpx; position: absolute;">
			<view style="padding: 20rpx;">
				<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC; background: #fff;">
					<u-form>
						<u-form-item label="路线" label-width="150rpx" >
							<u-input type="text" v-model="form.line"/>
						</u-form-item>
						<u-form-item label="乘客姓名" label-width="150rpx" >
							<u-input type="text" v-model="form.name"/>
						</u-form-item>
						<u-form-item label="手机号" label-width="150rpx" >
							<u-input type="text" v-model="form.phone"/>
						</u-form-item>
						<u-form-item label="上车时间" label-width="150rpx" >
							<uni-datetime-picker type="datetime" v-model="form.time"></uni-datetime-picker>
						</u-form-item>
						<u-form-item label="起点" label-width="150rpx" >
							<u-input type="select" v-model="form.star" @click="show = true"/>
							<u-picker v-model="show" mode="selector" :range="list" @confirm="get" rangeKey="name"></u-picker>
							
						</u-form-item>
						<u-form-item label="终点" label-width="150rpx" >
							<u-input type="select" v-model="form.end" @click="sshow = true"/>
							<u-picker v-model="sshow" mode="selector" :range="list" @confirm="sget" rangeKey="name"></u-picker>
						</u-form-item>
					</u-form>
				</view>
				
			</view>
		</view>
		<button @click="tl"  style="position: fixed; bottom: 0; border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#F62D59,#FF2D69); color: #fff; margin: 30rpx auto;">下一步</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[],
				
				sshow:false,
				show:false,
				form:{
					line:'',
					name:'',
					phone:'',
					star:'',
					end:'',
					time:''
				}
			}
		},
		methods: {
			get(e){
				this.form.star = this.list[e].name
			},
			sget(e){
				this.form.end = this.list[e].name
			},
			tl(){
				if(this.form.star == "" || this.form.end == ""){
					this.et('请选择上车或下车地点')
					return
				}
				this.so("bfor",this.form)
				uni.navigateTo({
					url: '/pages/service/bus/moreBX/moreBTJ',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		onLoad(e) {
			uni.request({
				url: this.gp()+'/prod-api/api/bus/stop/list',
				method: 'GET',
				data: {
					linesId:e.id
				},
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
			uni.request({
				url: this.gp()+'/prod-api/api/bus/line/'+e.id,
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.form.line = res.data.data.name 
					}
					
					console.log(this.slist)
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/api/common/user/getInfo',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.form.name = res.data.user.nickName
						this.form.phone = res.data.user.phonenumber
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
