<template>
	<web-view v-if="status == 1" src="https://m.baidu.com/bh/m/detail/ar_8522856339686958734"></web-view>
	<web-view v-else-if="status == 2" src="https://m.baidu.com/bh/m/detail/ar_11576036710414412797"></web-view>
	<web-view v-else-if="status == 3" src="https://health.baidu.com/m/detail/ar_16237602205435782522"></web-view>
	<web-view v-else-if="status == 4" src="https://m.baidu.com/bh/m/detail/ar_3825096602611270254"></web-view>
	<web-view v-else-if="status == 5" src="https://www.yjbys.com/xinli/ceshi/132979.html"></web-view>
	<web-view v-else-if="status == 6" src="https://m.gmw.cn/baijia/2020-01/09/1300866090.html"></web-view>
	<web-view v-else-if="status == 7" src="https://baijiahao.baidu.com/s?id=1707144499812339211&wfr=spider&for=pc"></web-view>
</template>

<script>
	export default {
		data() {
	
			return {
				status:0,
			};
		},
		onLoad() {
			this.status = uni.getStorageSync('itemData');;
			console.log(this.status);
			// setTimeout(() => {
			// 	uni.setNavigationBarTitle({
			// 		title: "早期脑瘤症状"
			// 	})
			// }, 2000)
		}
	}
</script>

<style>
</style>