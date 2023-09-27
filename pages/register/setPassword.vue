<template>
	<view class="container">
		<view class="top">
			<text id="title">设置密码</text>
			<text id="tips">请设置您的登录密码</text>
		</view>
		<view class="info">
			<u-form :model="form" ref="uForm">
				<u-form-item prop="password"><u-icon name="lock" color="#2979ff" size="28"></u-icon>
					<u-input v-model="form.password" placeholder="请输入密码" class="login-input" /></u-form-item>
				<u-form-item prop="password"><u-icon name="lock" color="#2979ff" size="28"></u-icon>
					<u-input v-model="form.rePassword" placeholder="请再次输入密码" class="login-input" /></u-form-item>
				<u-form-item><u-button @click="register" class="login-button">完成注册</u-button></u-switch></u-form-item>
			</u-form>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				form: {
					password: '',
					rePassword: ''
				},
				rules: {
					password: [{
						required: true,
						message: '请输入密码',
						trigger: ['blur'],
					}],
					rePassword: [{
						required: true,
						message: '请再次输入密码',
						trigger: ['blur'],
					}]
				}
			}
		},
		methods: {
			register() {
				
			}
		},
		onReady() {
			this.$refs.uForm.setRules(this.rules);
		}
	}
</script>


<style lang="less" scoped>
	.container {
		display: flex;
		justify-content: center;
		flex-direction: column;
		align-items: center;

		.top {
			display: flex;
			flex-direction: column;
			justify-content: left;
			width: 75vw;

			#title {
				font-size: 30px;
				font-weight: bold;
				margin-top: 10px;
			}

			#tips {
				font-weight: 600;
				margin-top: 10px;
			}
		}

		.info {
			margin-top: 30px;
			width: 75vw;
			.login-input {
				border: none;
				padding: 10px;
				border-bottom: 1px solid #f7ecdf;
			}
			
			.login-button {
				margin-top: 40px;
				background-color: #2979ff;
				color: #fff;
				text-align: center;
				border-radius: 20px;
				font-size: 17px
			}
		}
	}
</style>