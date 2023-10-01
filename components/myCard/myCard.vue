<template>
	<view class="card">
		<image src="your-image-url.jpg" alt="Card Image" class="card-image" mode="aspectFit"></image>
		<view class="card-content">
			<text class="card-title">Card Title</text>
			<view class="card-subtitle-text">
				<text class="card-subtitle">Subtitle</text>
				<text class="card-text">
					This is the content of the card. You can put any text or elements here.
				</text>
			</view>
		</view>
		<view class="card-buttons">
			<button class="card-button" @tap="handleButtonClick">Button 1</button>
			<button class="card-button" @tap="handleButtonClick">Button 2</button>
			<button class="card-button" @tap="handleButtonClick">Button 3</button>
		</view>
	</view>
</template>

<script>
	export default {
		name: "myCard",
		data() {
			return {

			};
		},
		methods: {
			handleButtonClick() {
				uni.showToast({
					title: 'Button Clicked!',
					icon: 'none'
				});
			}
		}
	}
</script>

<style lang="less" scoped>
	.card {
		display: flex;
		align-items: center;
		justify-content: space-between;
		/* 将内容水平分散对齐 */
		border: 1px solid #ccc;
		border-radius: 5px;
		padding: 10px;
		margin: 10px;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
	}

	.card-image {
		max-width: 100px;
		margin-right: 10px;
	}

	.card-content {
		flex: 1;
		/* 占满剩余空间 */
	}

	.card-title {
		font-weight: bold;
		font-size: 18px;
	}

	.card-subtitle-text {
		display: flex;
		align-items: center;
		margin-top: 10px;
	}

	.card-subtitle {
		color: #555;
		font-size: 14px;
	}

	.card-text {
		margin-left: 10px;
		/* 增加一些间距 */
	}

	.card-buttons {
		display: flex;
		justify-content: flex-end;
		/* 按钮右对齐 */
		align-items: center;
		margin-top: 10px;
	}

	.card-button {
		margin-left: 10px;
		/* 为按钮增加一些间距 */
	}
</style>