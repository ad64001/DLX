<template>
	<view style="padding: 20rpx;">
		<view style="width: 100%; display: flex; margin-top: 20rpx;">
			<view style="width: 30%;">
				<uni-list>
					<uni-list-item  v-for="(item,index) in list" :key="index" >
						<view slot="header" @click="toi(index)">
							<view :class="index == current?'aut':''">{{item.name}}</view>
						</view>
					</uni-list-item>
				</uni-list>
			</view>
			<view style="width: 70%;">
				<uni-card title="种类" :isFull="true" style="border-right: 0 30rpx 0 30rpx;">
					<uni-grid :column="3" :showBorder="false" :highlight="false">
						<uni-grid-item v-for="item in 15">
							<view style="margin: 20rpx auto;" @click="tose(item.serviceName)">
								<view style="display: flex; margin: auto; width: 100rpx; height: 100rpx; background: #eee;border-radius: 100rpx;">
									<image style="margin: auto; width: 70rpx; height: 70rpx; background: #eee; "  mode=""></image>
								</view>
								<view style="width:170rpx; text-align: center;font-weight: bold; margin: auto;">电池</view>
							</view>
						</uni-grid-item>
					</uni-grid>
				</uni-card>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[{name:'分类示例'},{name:'分类示例'},{name:'分类示例'},{name:'分类示例'},{name:'分类示例'},{name:'分类示例'},{name:'分类示例'}],
				current:0
			}
		},
		methods: {
			toi(e){
				this.current = e
			}
		}
	}
</script>

<style>

</style>
