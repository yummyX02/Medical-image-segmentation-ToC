<template>
	<view class="container">
		<view class="top">
			<h2>就诊人管理</h2>
			<h3>您可以修改就诊人的手机号码</h3>
		</view>
		<view class="mid">
			<text class="fix">姓名</text>
			<text class="info">
				{{this.info.patient}}
				<text class="spe">|</text>
				<text>{{this.info.sex}}
					<text class="spe">|</text>
					<text>{{this.info.age}}</text>
				</text>
			</text>
			<text class="fix">证件号码</text>
			<text class="info">
				身份证
				<text class="spe">{{this.info.identify}}</text>
			</text>
			<text class="fix">手机号码</text>
			<text class="info identification">{{this.info.phone}}</text>
			<u--input placeholder="验证码" border="surround" v-model="value" class="ipt" @change="change"></u--input>
		</view>
		<view class="footer">
			<button class="left">删除就诊人</button>
			<button class="right">保存</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				info: {},
				value: "",
			};
		},
		mounted() {
			uni.getStorage({
				key: "patientInfo",
				success: (res) => {
					this.info = res.data;
				},
			});
		}
	}
</script>

<style lang="less">
	.container {
		.top {
			padding: 30px;
			margin: 0 15px 0 15px;
		}

		.mid {
			padding: 30px;
			display: flex;
			flex-direction: column;
			margin: 0 15px 0 15px;

			.fix {
				padding: 5px;
				font-size: 13px;
				color: darkgray;
				margin-top: 20px;
			}

			.info {
				padding: 5px;
				font-size: 20px;

			}

			.spe {
				margin-right: 5px;
				margin-left: 5px;
			}

			.identification {
				border-bottom: 1px solid #0379ff;
			}

			.ipt {
				border: none;
				border-bottom: 1px solid #ccc;
				padding: 10px;
				margin-top: 20px;
				transition: border-color 0.3s;
				/* 添加过渡效果 */

				/* 选中状态下的边框样式 */
				&:focus {
					border-bottom: 1px solid #0379ff;
					/* 选中状态下的边框颜色 */
					outline: none;
					/* 移除默认的选中时的外边框 */
				}
			}
		}

		.footer {
			display: flex;
			align-items: center;
			justify-content: center;
			margin-top: 100px;

			.left {
				width: 200px;
				color: #b1a5a6;
				background-color: #fff;
				border-radius: 20px;
				border: none;
			}

			.right {
				color: #fff;
				background-color: #0379ff;
				width: 200px;
				border-radius: 20px;
			}

		}
	}
</style>