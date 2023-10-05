<template>
	<view class="container">
		<topBar></topBar>
		<view class="top">
			<h3  class="title">CT图像</h3>
			<view class="card">
				暂无
			</view>
		</view>
		<view class="mid">
			<h3  class="title">医生建议</h3>
			<view class="card">
				暂无
			</view>
		</view>
		
		<view class="footer">
			<h1>祝您生活健康</h1>
			<img src="../../static/bgc-report.png" alt="">
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="less">
.container{

	background-color: #f7f8ff;
	.title {
	  margin-left: 30px; /* 距离左边 15px */
	  margin-top: 10px;
	}
	
	.card {
	  text-align: left; 
	  border: 1px solid #ccc; /* 添加边框样式 */
	  padding: 10px;
	  width: 85vw;
	  margin-left: 30px;
	  margin-top: 10px;
	  border-radius: 10px;
	  border: none;
	  background-color: #fff;
	}
	.footer {
		margin-top: 8vh;
	  display: flex;
	  flex-direction: column;
	  justify-content: center; /* 水平居中 */
	  align-items: center; /* 垂直居中 */
	}
	
	.footer img {
	  max-width: 100%; /* 最大宽度为容器宽度 */
	  max-height: 100%; /* 最大高度为容器高度 */
	  width: auto; /* 自动调整宽度 */
	  height: auto; /* 自动调整高度 */
	}
}
</style>
