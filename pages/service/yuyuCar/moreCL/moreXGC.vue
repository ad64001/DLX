<template>
	<view>
		<view style="width: 100%;height: 300rpx; background: linear-gradient(180deg,#00dee5,#00eee5);">
			<view style="padding: 20rpx;">
				<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC; background: #fff;">
					<u-form>
						<u-form-item label="车架号" label-width="150rpx" >
							<u-input v-model="form.engineNo"  placeholder="请输入你的车架号"/>
						</u-form-item>
						<u-form-item label="车牌号" label-width="150rpx" >
							<u-input v-model="form.plateNo" placeholder="请输入你的车牌号"/>
						</u-form-item>
						<u-form-item label="号牌类型" label-width="150rpx" >
							<u-input v-model="form.type" placeholder="请输入你的号牌类型"/>
						</u-form-item>
					</u-form>
				</view>
				<button @click="tot" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#00dee5,#00eee5); color: #fff; margin: 30rpx auto;">确认</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				form:{
					engineNo:'',
					plateNo:'',
					type:''
				},
				id:''
			}
		},
		methods: {
			tot(){
				uni.request({
					url: this.gp()+'/prod-api/api/traffic/car',
					method: 'PUT',
					data: {
						id:this.id,
						engineNo:this.form.engineNo,
						plateNo:this.form.plateNo,
						type:this.form.type
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
		},
		onLoad(e) {
			this.id = e.id
		}
	}
</script>

<style>

</style>
