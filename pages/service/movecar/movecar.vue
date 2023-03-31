<template>
	<view>
		<view style="width: 100%; height: 300rpx; background:linear-gradient(180deg,#22c876,#22b876); border-radius: 0 0 30rpx 30rpx;">
			<view style="padding: 20rpx;">
				<view style="margin-top: 20rpx; padding: 30rpx;width: 100%; border-radius: 30rpx; box-shadow:  0 0 25rpx #CCC; background: #fff;">
					<u-form>
						<u-form-item label="详细地址" label-width="150rpx" >
							<view>{{sf}}</view><view v-show="sf.length == 0">省</view><u-icon @click="show = true" name="arrow-down"></u-icon>
							<view>{{cs}}</view><view v-show="cs.length == 0">市</view><u-icon @click="sshow = true" name="arrow-down"></u-icon>
							<view>{{qu}}</view><view v-show="qu.length == 0">区</view><u-icon @click="ssshow = true" name="arrow-down"></u-icon>
							<u-picker v-model="show" mode="selector" :range="list" @confirm="get" rangeKey="name"></u-picker>
							<u-picker v-model="sshow" mode="selector" :range="slist" @confirm="sget" rangeKey="name"></u-picker>
							<u-picker v-model="ssshow" mode="selector" :range="sslist" @confirm="ssget" rangeKey="name"></u-picker>
						</u-form-item>
						<u-form-item label="身份证" label-width="150rpx" >
							<u-input v-model="idc"  placeholder="请输入你的身份证"/>
						</u-form-item>
						
						<u-form-item label="车牌号" label-width="150rpx" >
							<u-input v-model="carno" placeholder="请输入车牌号"/>
						</u-form-item>
						<u-form-item label="联系电话" label-width="150rpx" >
							<u-input v-model="phone" placeholder="请输入你的电话号码"/>
						</u-form-item>
						<u-form-item label="现场照片" label-width="150rpx" >
							<image @click="chooseImage " style="width: 200rpx; height: 200rpx; background: #CCC;" :src="images"></image>
						</u-form-item>
					</u-form>
				</view>
				<button @click="tl" style="border-radius: 20rpx; width: 100%; height: 100rpx; background: linear-gradient(90deg,#22c876,#22b876); color: #fff; margin: 30rpx auto;">提交申请</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				show:false,
				list:[],
				sf:'',
				slist:[],
				sshow:false,
				cs:'',
				ssshow:false,
				sslist:[],
				qu:'',
				idc:'',
				carno:'',
				phone:'',
				images:null
				
			}
		},
		methods: {
			get(e){
				this.sf = this.list[e].name
				uni.request({
					url: this.gp()+'/prod-api/api/common/gps/city',
					method: 'GET',
					data: {
						provinceName:this.list[e].name
					},
					success: res => {
						console.log(res)
						if(res.data.code == 200){
							this.slist = res.data.data
						}
					},
					fail: () => {},
					complete: () => {}
				});
			},
			sget(e){
				this.cs = this.slist[e].name
				uni.request({
					url: this.gp()+'/prod-api/api/common/gps/are',
					method: 'GET',
					data: {
						provinceName:this.sf,
						cityName:this.slist[e].name
					},
					success: res => {
						console.log(res)
						if(res.data.code == 200){
							this.sslist = res.data.data
						}
					},
					fail: () => {},
					complete: () => {}
				});
			},
			ssget(e){
				this.qu = this.sslist[e].name
			},
			chooseImage(){
				uni.chooseImage({
					count:1,
					success:res=>{
						this.images = res.tempFilePaths[0] 
					}
				})
			},
			tl(){
				uni.uploadFile({
					url:this.gp()+'/prod-api/common/upload',
					filePath:this.images,
					name:'file',
					header:this.th(),
					success: (res) => {
						uni.request({
							url: this.gp()+'/prod-api/api/park/car/move',
							method: 'POST',
							data: {
								province:this.sf,
								city:this.cs,
								area:'天河区',
								idCard:this.idc,
								plateNo:this.carno,
								tel:this.phone,
								photo:this.gp()+JSON.parse(res.data).fileName
							},
							header:this.th(),
							success: res1 => {
								this.et(res1.data.msg)
								console.log(res1)
								if(res.data.code == 200){
									
								}
							},
							fail: () => {},
							complete: () => {}
						});
					}
				})
			}
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/common/gps/province',
				method: 'GET',
				data: {},
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.list = res.data.data
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
