<template>
	<view class="container">
		<view class="top">
			<view class="nav" @click="navigator">
				<u-icon name="arrow-left" size="28"></u-icon>
			</view>
			<view class="info">
				<u-steps current="1" activeIcon="checkmark-circle-fill">
					<u-steps-item title="待就诊" iconSize="50px"></u-steps-item>
					<u-steps-item title="开具处方" iconSize="50px"></u-steps-item>
					<u-steps-item title="就诊完成" iconSize="50px"></u-steps-item>
				</u-steps>
			</view>
			<view class="bottom">
				<text style="color: aliceblue;">预约挂号成功，请就诊日当日打开APP等待医生呼叫</text>
			</view>
		</view>
		<view class="doctor">
			<view class="info-top">
				<view class="left">
					<img style="width: 60px;height: 80px;" src="../../static/doctor2.jpg" alt="" srcset="">
				</view>
				<view class="right">
					<view class="title">
						<h2>{{name}}</h2>
						<h3>{{degree}}</h3>
					</view>
					<view class="identify">
						{{identify}}
					</view>
				</view>
			</view>
			<view class="mid">
				<view class="list">
					<text class="titleText">就诊医院科室</text>
					<text>{{office}}</text>
				</view>
				<view class="list">
					<text class="titleText">门诊时间</text>
					<text>{{time}}</text>
				</view>
				<view class="list">
					<text class="titleText">门诊类型</text>
					<text>{{type}}</text>
				</view>
				<view class="list">
					<text class="titleText">医师服务费</text>
					<text>{{money}}</text>
				</view>
			</view>
			<view class="bottom">
				<view class="title">
					<u-icon name="info-circle-fill" color="#ffa905"></u-icon>
					<text style="color: #ffa905;">门诊预约挂号须知</text>
					<text style="margin-left: 5px;color: #d1cfc6;">(预约即代表同意以下规则)</text>
				</view>
				<text style="margin-top: 5px;font-weight: bold;color: darkgray;">1.医事服务费由医院设定本平台不收取任何额外费用</text>
				<text style="margin-top: 5px;font-weight: bold;color: darkgray;">2.停诊将短信通知，请保持手机畅通</text>
				<text style="margin-top: 5px;font-weight: bold;color: darkgray;">3.实名制预约，就诊人信息不符将无法取号</text>
				<text
					style="margin-top: 5px;font-weight: bold;color: darkgray;">4.门诊为网上就诊，届时医生将拨打患者网络电话，如无法在规定时间内接听视为<text
						style="color: red;">爽约</text></text>
				<view class="line">
					<view class="left">
						<h4>预计网上问诊时间</h4>
						<text style="margin-top: 10px;color: #d1cfc6;">请打开APP并保证网络流畅</text>
					</view>
					<view class="right">
						<h2>{{date}}
						</h2>
						<h2>{{detailtime}}</h2>
					</view>
				</view>
			</view>
		</view>
		<view class="info-bottom">
			<h3 style="color: #d1cfc6;">就诊人:</h3>
			<view class="patient-card">
				<view class="title">
					<h2>{{patient.name}}</h2>
					<text>{{patient.sex}}</text>
					<text>|</text>
					<text>{{patient.age}}</text>
				</view>
				<view class="detail">
					<view class="li">
						<text style="color: #d1cfc6;">医保卡号</text>
						<text>{{card}}</text>
					</view>
					<view class="li">
						<text style="color: #d1cfc6;">报销类型</text>
						<text>医保报销</text>
					</view>
				</view>
			</view>
		</view>
		<view class="btn">
			<button @click="cancel">取消预约</button>
			<button @click="navigato">返回首页</button>
			<u-notify message="取消预约成功!" :show="show"></u-notify>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				identify: "北京协和医院博士生导师",
				name: "王医生",
				degree: "主任医师",
				office: "北京协和医院-神经内科",
				type: "互联网门诊",
				money: "318元",
				date: "5月5日",
				detailtime: "15:00-16:30",
				time: "2020年05月05日 周四下午",
				phone: "18791881394",
				card: "YBK1231231231211",
				patient:{
					name: "王戈",
					sex: '男',
					age: "30岁"
				},
				show:false
			};
		},
		methods: {
			navigator() {
				uni.navigateBack()
			},
			cancel(){
				this.show = true;
			},
			navigato(){
				uni.navigateTo({
					url:'/pages/index/home'
				})
			}
		}
	}
</script>

<style lang="less">
	.container {
		background-color: #f7f8ff;

		.top {
			height: 160px;
			background-color: #0379ff;

			.info {
				margin-top: 20px;
			}

			.bottom {
				text-align: center;
				margin-top: 20px;
				font-weight: bold;
			}
		}
	}

	::v-deep .info {
		.u-steps-item__content {
			.u-text__value {
				font-size: 23px !important;
				margin-top: 10px;
				color: aliceblue;
				font-weight: bold;
			}
		}
	}

	.info-bottom {
		background-color: #fff;
		margin: 5px 25px 25px 25px;
		padding: 10px;
		.patient-card{
			.title{
				display: flex;
				align-items: center;
				border-bottom: 1px solid darkgray;
				padding: 5px;
				text,h2{
					margin-right: 10px;
				}
			}
			.detail{
				display: flex;
				flex-direction: column;
				.li{
					display: flex;
					justify-content: space-between;
					margin-top: 5px;
				}
			}
		}
	}
.btn{
	display: flex;
	button{
		width: 200px;
		height: 40px;
		border-radius: 20px;
		background-color: #0379ff;
		margin-bottom: 20px;
		text-align: center;
	}
}
	.doctor {
		margin: 25px;
		background-color: #fff;
		border-radius: 10px;

		.info-top {
			display: flex;
			padding: 5px;
			margin: 20px;

			.right {
				margin-left: 40px;

				.title {
					display: flex;
					align-items: center;

					h3 {
						margin-left: 10px;
					}

				}

				.identify {
					margin-top: 20px;
					color: darkgray;
				}
			}
		}

		.mid {
			padding: 0px 10px 10px 10px;
			border-top: 2px solid #bbbcbe;
			border-bottom: 2px solid #bbbcbe;

			.list {
				display: flex;
				justify-content: space-between;
				padding: 5px;

				.titleText {
					color: #bbbcbe;
				}
			}
		}

		.bottom {
			display: flex;
			flex-direction: column;
			padding: 5px;

			.title {
				display: flex;
				margin-top: 8px;
				align-items: center;
			}

			.line {
				display: flex;
				align-items: center;
				justify-content: space-between;
				margin-top: 10px;
				padding-top: 10px;
				border-top: 1px solid darkgray;

				.right {
					display: flex;
				}
			}

		}


	}
</style>