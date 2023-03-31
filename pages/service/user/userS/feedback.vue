<template>
	<view style="padding: 20rpx;">
		<view style="width: 100%;border-radius: 20rpx; box-shadow:  0 0 20rpx #ccc;">
			<u-field label="反馈标题" v-model="titl" placeholder="请输入您的反馈" />
			<uni-card title="反馈内容" style="border-radius: 20rpx;" :isFull="true">
				<textarea maxlength="150" v-model="msg" style="width: 100%;" @input="fors"></textarea>
				<text>{{s}}/150</text>
			</uni-card>
		</view>
		<button @click="tl" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#00d0f0,#00a0f0); color: #fff; margin: 5vh auto;">确认</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				titl:'',
				msg:'',
				s:0
			}
		},
		methods: {
			fors(e){
				this.s = e.detail.value.length 
			},
			tl(){
				uni.request({
					url: this.gp()+'/prod-api/api/common/feedback',
					method: 'POST',
					data: {
						"content": this.msg,
						"title": this.titl
					},
					header:this.th(),
					success: res => {
						this.et(res.data.msg)
						console.log(res)
						if(res.data.code == 200){
							this.et('反馈成功')
							setTimeout(res=>{
								uni.navigateBack();
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
