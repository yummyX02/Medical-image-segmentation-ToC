<template>
	<view class="container">
		<view class="title">
			智医
		</view>
		<view class="info">
			<u-form :model="form" ref="uForm">
				<u-form-item><u-icon name="phone" color="#2979ff" size="28"></u-icon>
					<u-input v-model="form.phone" placeholder="请输入手机号码" class="login-input" /></u-form-item>
				<u-form-item><u-icon name="lock" color="#2979ff" size="28"></u-icon>
					<u-input v-model="form.password" placeholder="请输入密码" class="login-input" /></u-form-item>
				<u-form-item><u-button @click="login" class="login-button">登录</u-button></u-switch></u-form-item>
			</u-form>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				form: {
					phone: '',
					password: '',
				}
			};
		},
		methods:{
			login(){
				console.log("开始登录");
			}
		}
	}
</script>

<style lang="less">
	.container {
		.title {
			font-size: 30px;
			text-align: center;
			color: #2979ff;
		}

		.info {
			height: 30vh;
			display: flex;
			justify-content: center;
			align-items: center;
			margin-top: 60px;
			.login-input {
				border: none;
				padding: 10px;
				border-bottom: 1px solid #f7ecdf;
			}
			.login-button{
				margin-top: 40px;
				background-color: #2979ff;
				color: #fff;
				text-align: center;
				border-radius: 20px;
			}
		}
	}
</style>