<template>
	<view>
		<view style="margin-top: 30rpx;">
			<view>
				<uni-list>
					<uni-list-item :title="item.categoryName" v-for="item in slist" link="navigateTo" :to="'moreX?id='+item.categoryName+'&&it='+item.id"></uni-list-item>
				</uni-list>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				slist:[],
			}
		},
		methods: {
			
		},
		onLoad() {
			uni.request({
				url: this.gp()+'/prod-api/api/hospital/category/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.slist = res.data.rows
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
