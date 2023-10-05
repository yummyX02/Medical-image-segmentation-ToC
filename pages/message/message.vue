<template>
	<!-- //页面12 -->
	<view class="container">
		<div class="card">
			<div class="left">
				<u-icon name="question-circle-fill"></u-icon>
			</div>
			<div class="right">
				<view class="top">
					<h3 class="title">标题</h3>
					<div class="date">2023-10-05</div>
				</view>
				<span class="text">这是一段小号文字</span>
			</div>
		</div>
		<div class="card">
			<div class="left">
				<u-icon name="question-circle-fill"></u-icon>
			</div>
			<div class="right">
				<view class="top">
					<h3 class="title">标题</h3>
					<div class="date">2023-10-05</div>
				</view>
				<span class="text">这是一段小号文字</span>
			</div>
		</div>
		<div class="card">
			<div class="left">
				<u-icon name="question-circle-fill"></u-icon>
			</div>
			<div class="right">
				<view class="top">
					<h3 class="title">标题</h3>
					<div class="date">2023-10-05</div>
				</view>
				<span class="text">这是一段小号文字</span>
			</div>
		</div>
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
	.container {
		display: flex;
		flex-direction: column;
		margin-top: 20px;
		align-items: center;
	}

	.card {
		display: flex;
		align-items: center;
		border: 1px solid #ccc;
		padding: 10px;
		box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2);
		/* 添加立体效果 */
		transition: box-shadow 0.3s ease;
		/* 添加过渡效果 */
		width: 80vw;
		border: none;
		border-radius: 10px;
		margin-top: 20px;
	}

	.card:hover {
		box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3);
		/* 鼠标悬停时增加更强的立体效果 */
	}

	.left {
		margin-right: 10px;
	}

	.icon {
		/* 添加图标样式，可以使用字体图标或图片 */
		font-size: 24px;
	}

	.right {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		margin-left: 20px;
	}

	.title {
		font-size: 18px;
		margin: 0;
	}

	.date {
		color: #666;
		font-size: 14px;
	}

	.text {
		color: #666;
		font-size: 12px;
		margin-top: 10px;
	}
	.top{
		display: flex;
		justify-content: space-between;
		width: 65vw;
	}
</style>