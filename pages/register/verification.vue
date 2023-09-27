<template>
	<view class="container">
		<view class="top">
			<text id="title">输入验证码</text>
			<text id="tips">验证码已发送至{{phone}}</text>
		</view>
		<view class="info">
			<u-form :model="form" ref="uForm">
				<u-form-item prop="code" class="myForm">
					<u-input class="myinput" v-model="form.code[0]" type="number" maxlength="1" />
					<u-input class="myinput" v-model="form.code[1]" type="number" maxlength="1" />
					<u-input class="myinput" v-model="form.code[2]" type="number" maxlength="1" />
					<u-input class="myinput" v-model="form.code[3]" type="number" maxlength="1" />
					<u-input class="myinput" v-model="form.code[4]" type="number" maxlength="1" />
					<u-input class="myinput" v-model="form.code[5]" type="number" maxlength="1" />
				</u-form-item>
				<u-form-item><text class="resend" @click="resent">重新发送</text></u-form-item>
				<u-form-item><u-button @click="send" class="login-button">下一步</u-button></u-switch></u-form-item>
			</u-form>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				phone: '',
				form: {
					code: ['','','','','',''],
				},
				rules: {
					code: [{
						required: true,
						message: '请输入验证码',
						trigger: ['blur'],
					}]
				}
			}
		},
		methods:{
			resent(){
				// 同登录
			}
		},
		onLoad() {
			uni.$on("sendPhone", function(data) {
				console.log("传递的手机号码：", data);
				this.phone = data;
			})
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

			.myForm {
				display: flex;
				flex-direction: column;
				justify-content: center;
				align-items: center;

				.verification-code {
					display: flex;
					justify-content: space-between;
					align-items: center;
				}

			}

			.login-button {
				margin-top: 30px;
				background-color: #2979ff;
				color: #fff;
				text-align: center;
				border-radius: 20px;
				font-size: 17px;
				width: 100%;
				/* 调整按钮的宽度 */
			}
			.resend{
				color: #ffab10;
			}

		}
	}
</style>