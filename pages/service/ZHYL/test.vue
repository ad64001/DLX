<template>
  <view>
	  
  </view>
</template>

<script>
  export default {
  	data() {
  		return {
  			opts:{
  			  xAxis:{
					boundaryGap:"justify"
				}
			},
			option:{
				categories:["1月","2月","3月","4月","5月","6月","7月"],
				series:[
					{
					name:"成交量A",
					data:[0,23,85,69,23,45,74]
					},
					{
					name:"成交量B",
					data:[0,53,65,29,53,85,94]
					},
				]
			}
  		}
  	},
  	methods: {
  		
  	}
  }
</script>

<style scoped>
  /* 请根据实际需求修改父元素尺寸，组件自动识别宽高 */
 
</style>