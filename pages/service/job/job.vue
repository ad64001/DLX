<template>
	<view style="padding: 20rpx;">
		<view>
			 <u-subsection active-color="#ff9900" :list="list" @change="che" :current="current"></u-subsection>
		</view>
		<view v-show="current == 0">
			<view>
				<uni-search-bar/>
			</view>
			<view>
				<u-swiper>
				</u-swiper>
			</view>
			<view>
				<view style="margin-top: 20rpx;">
					<u-section title="热门岗位" lineColor="#ff9900" :right="false"></u-section>
				</view>
			</view>
			<view style="margin-top: 20rpx;">
				<u-tabs :list="slist" @change="che1" :current="current1"></u-tabs>
			</view>
			<view>
				<uni-card @click="tls(item.id)" v-for="item in sslist" :isFull="true" :note="'公司地址:'+item.address" :title="item.name" style="margin-top: 20rpx; border: 1rpx solid #ccc; border-radius: 30rpx; color: #666666;">
					<view>职位需求:{{item.need}}</view>
					<view>薪资待遇:{{item.salary}}</view>
					<view>岗位职责:{{item.obligation}}</view>
				</uni-card>
			</view>
			
		</view>
		<view v-show="current == 1">
			<view>
				<view style="margin-top: 20rpx;">
					<u-section title="简历投送历史" lineColor="#ff9900" :right="false"></u-section>
				</view>
			</view>
			<view>
				<uni-card @click="tls(item.id)" v-for="item in sssslist.slice(inds,indx)" :isFull="true" :title="item.companyName" style="margin-top: 20rpx; border: 1rpx solid #ccc; border-radius: 30rpx; color: #666666;">
					<view>岗位名称:{{item.postName}}</view>
					<view>薪资:{{item.money}}</view>
					<view>投递时间:{{item.satrTime}}</view>
				</uni-card>
			</view>
			<view style="margin-top: 10rpx; margin-bottom: 10rpx;">
				<uni-pagination :total="sssslist.length" pageSize="10" current="1" @change="ches"></uni-pagination>
			</view>
			
		</view>
		<view v-show="current == 2">
			<view>
				<view style=" padding: 20rpx; width: 100%; height: 300rpx; background: linear-gradient(180deg,#FFA755,#FF7BA5);">
					<image style="display: flex; width: 150rpx; height: 150rpx; border-radius: 100rpx; background: #eee; margin: 30rpx auto;" src="../../../static/hb/kele.png" mode=""></image>
					<view style="display: block; color: #fff; text-align: center; font-size: 35rpx; margin-bottom: 20rpx;">你好{{list.nickName}}</view>
				</view>
				<view style="margin-top: 10rpx;">
					<uni-list>
						<uni-list-item :clickable="true">
							<view slot="header" style="display: flex; font-size: 35rpx;">
								<u-icon name="account"></u-icon>
								<view style="margin-left: 30rpx;">
									<view>{{ssslist.userName}}</view>
								</view>
							</view>
						</uni-list-item>
						<uni-list-item :clickable="true" >
							<view slot="header" style="display: flex; font-size: 35rpx;">
								<u-icon name="kefu-ermai"></u-icon>
								<view style="margin-left: 30rpx;">
									<view>{{ssslist.idCard}}</view>
								</view>
							</view>
						</uni-list-item>
						<uni-list-item :clickable="true" >
							<view slot="header" style="display: flex; font-size: 35rpx;">
								<u-icon name="email"></u-icon>
								<view style="margin-left: 30rpx;">
									<view>{{ssslist.email}}</view>
								</view>
							</view>
						</uni-list-item>
						<uni-list-item :clickable="true" >
							<view slot="header" style="display: flex; font-size: 35rpx;">
								<u-icon name="phone"></u-icon>
								<view style="margin-left: 30rpx;">
									<view>{{ssslist.phonenumber}}</view>
								</view>
							</view>
						</uni-list-item>
						
					</uni-list>
				</view>
				<button @click="tl(ssslist.userId)" style="border-radius: 20rpx; width: 60%; height: 100rpx; background: linear-gradient(90deg,#FFA755,#FF7BA5); color: #fff; margin: 200rpx auto;">新增学历</button>
			</view>
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[{name:'找工作'},{name:'简历投递'},{name:'我的简历'}],
				current:0,
				slist:[],
				current1:0,
				sslist:[],
				ssslist:{},
				sssslist:[],
				inds:0,
				indx:10
			}
		},
		methods: {
			che(e){
				this.current = e
			},
			che1(e){
				this.current1 = e
				uni.request({
					url: this.gp()+'/prod-api/api/job/post/list',
					method: 'GET',
					data: {
						professionId:this.slist[e].id
					},
					header:this.th(),
					success: res => {
						if(res.data.code == 200){
							this.sslist = res.data.rows
						}
					},
					fail: () => {},
					complete: () => {}
				});
			},
			tl(e){
				uni.navigateTo({
					url: 'moreNJL/moreNJL?id='+e,
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			},
			tls(e){
				uni.navigateTo({
					url: '/pages/service/job/moreVN/moreVN?id='+e,
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			},
			ches(e){
				if(e.type == "next"){
					this.inds += 10
					this.indx += 10
				}else{
					this.inds -= 10
					this.indx -= 10
				}
			}
		},
		onLoad(){
			uni.request({
				url: this.gp()+'/prod-api/api/job/post/list',
				method: 'GET',
				data: {
					professionId:1
				},
				header:this.th(),
				success: res => {
					if(res.data.code == 200){
						this.sslist = res.data.rows
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
					// console.log(res)
					if(res.data.code == 200){
						for(let i of res.data.rows){
							this.slist.push({
								name:i.professionName,
								id:i.id
							})
						}
						
					}
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
					// console.log(res)
					if(res.data.code == 200){
						this.ssslist = res.data.user
					}
				},
				fail: () => {},
				complete: () => {}
			});
			uni.request({
				url: this.gp()+'/prod-api/api/job/deliver/list',
				method: 'GET',
				data: {},
				header:this.th(),
				success: res => {
					console.log(res)
					if(res.data.code == 200){
						this.sssslist = res.data.rows
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
