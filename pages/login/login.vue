<template>
	<view class="container">
		<view class="title">
			智医
		</view>
		<view class="info">
			<u-form :model="form" ref="uForm">
				<u-form-item prop="phone"><u-icon name="phone" color="#2979ff" size="28"></u-icon>
					<u-input v-model="form.phone" placeholder="请输入手机号码" class="login-input" /></u-form-item>
				<u-form-item prop="password"><u-icon name="lock" color="#2979ff" size="28"></u-icon>
					<u-input v-model="form.password" placeholder="请输入密码" class="login-input" /></u-form-item>
				<u-form-item><u-button @click="login" class="login-button">登录</u-button></u-switch></u-form-item>
			</u-form>
		</view>
		<view class="footer">
			<text class="noneID">没有账号？</text>
			<text class="register" @click="navigationToRegister">立即注册</text>
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
				},
				rules: {
					phone: [{
						required: true,
						message: '请输入手机号码',
						trigger: ['blur'],
					}],
					password: [{
						min: 5,
						message: '密码不能少于5位',
						trigger: 'change'
					}]
				},
				token:'',
			};
		},
		methods: {
			login() {
				console.log(this.form);
					uni.request({
						url:'http://localhost:5000/patient_login',
						method:'POST',
						data:{
							phone:this.form.phone,
							password:this.form.password,
						},
						header:{
							'token':''
						},
						success:(res) =>{
							console.log('resdata'+res.data.message);
							console.log('前端接收到的用户是'+res.data.username)
							
							if(res.data.status == 'success'){
								
								//存
								uni.setStorageSync('access_token',res.data.token)
								uni.setStorageSync('username',res.data.username)
								uni.setStorageSync('phone',this.form.phone)
								uni.switchTab({
									url:'/pages/index/home'
								})
							}
						}
						})
				
				
			},
			navigationToRegister(){
				console.log("去注册咯");
				uni.navigateTo({
					url:'/pages/register/register'
				})
			}
		},
		onReady() {
			this.$refs.uForm.setRules(this.rules);
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

			.login-button {
				margin-top: 40px;
				background-color: #2979ff;
				color: #fff;
				text-align: center;
				border-radius: 20px;
				font-size: 17px
			}
		}

		.footer {
			margin-top: 30px;
			display: flex;
			justify-content: center;
			align-items: center;
			font-size: 14px;

			.noneID {
				color: #bec4d6;
			}

			.register {
				color: #2979ff;
			}
		}
	}
</style>