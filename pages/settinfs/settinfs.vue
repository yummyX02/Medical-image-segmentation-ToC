<template>
	<view class="container">
		<view class="top">
			<view class="card">
				<div class="row">
					<span>账号设置</span>
					<u-icon name="arrow-right"></u-icon>
				</div>
				<div class="row">
					<span>消息通知</span>
					<u-icon name="arrow-right"></u-icon>
				</div>
				<div class="row">
					<span>地址管理</span>
					<u-icon name="arrow-right"></u-icon>
				</div>
				<div class="row">
					<span>缓存清理</span>
					<view style="display: flex;"><text>12.9M</text><u-icon name="arrow-right"></u-icon></view>
				</div>
			</view>
		</view>
		<view class="mid" style="margin-top: 30px;">
			<view class="card">
				<div class="row">
					<span>功能介绍</span>
					<u-icon name="arrow-right"></u-icon>
				</div>
				<div class="row">
					<span>法律声明</span>
					<u-icon name="arrow-right"></u-icon>
				</div>
				<div class="row">
					<span>用户服务协议</span>
					<u-icon name="arrow-right"></u-icon>
				</div>
				<div class="row">
					<span>隐私</span>
					<view style="display: flex;"><u-icon name="arrow-right"></u-icon></view>
				</div>
			</view>
		</view>
		<view class="bottom">
			<view class="card">
				<div class="row">
					<span>检查更新</span>
					<span style="color: darkgray;">版本号1.0.1</span>
				</div>
			</view>
		</view>
		<view class="footer">
			<button type="default">退出登录</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style lang="less" scoped>
	.container {
		background-color: #f7f8ff;

		.card {
			background-color: #fff;
			margin: 20px;
			border: none;
			border-radius: 10px;
			padding: 10px;
			margin: 30px;
			 box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.2); 
		}

		.row {
			display: flex;
			justify-content: space-between;
			align-items: center;
			border-bottom: 1px solid #ccc;
			padding: 10px 0;
		}

		.row:last-child {
			border-bottom: none;
		}

		.row span {
			font-weight: bold;
		}
		.footer {
			button{
				width: 70vw;
				border: none;
				background-color: #fff;
				color: #4aaaff;
				border-radius: 25px;
				 box-shadow: 0px 2px 5px rgba(74, 170, 255, 1); 
			}
		}
		
	}
</style>