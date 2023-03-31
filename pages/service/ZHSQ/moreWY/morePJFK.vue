<template>
	<view style="padding: 20rpx;">
		<view style="width: 100%;border-radius: 20rpx; box-shadow:  0 0 20rpx #ccc;">
			<u-field label="反馈标题" v-model="titl" placeholder="请输入您的反馈" />
			<uni-card title="反馈内容" style="border-radius: 20rpx;" :isFull="true">
				<textarea maxlength="150" v-model="msg" style="width: 100%;" @input="fors"></textarea>
				<text>{{s}}/150</text>
			</uni-card>
		</view>
		<button @click="tl" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#22c876,#00dee5); color: #fff; margin: 5vh auto;">确认</button>
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
			tl(){
				this.et('反馈成功')
				setTimeout(res=>{
					uni.navigateBack({
						delta: 1
					},400);
				})
			},
			fors(e){
				this.s = e.detail.value.length 
			}
		}
	}
</script>

<style>

</style>
