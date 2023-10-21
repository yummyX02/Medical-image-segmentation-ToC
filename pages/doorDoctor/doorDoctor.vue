<template>
	<view class="container">
		<view class="card-top">
			<view class="doctor">
				<view class="info-top">
					<view class="left">
						<img style="width: 60px;height: 80px;" src="../../static/doctor1.jpg" alt="" srcset="">
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
					<view class="line">

					</view>
				</view>
			</view>
		</view>
		<view class="card-bottom">
			<text style="color: darkgray;font-size: 18px;">选择就诊人</text>
			<view class="selPatients">
				<view class="patient" v-for="(item, index) in patientList" :key="index" @click="selectPatient(index)"
					:class="{ 'selected': selectedPatientIndex === index }">
					<h2>{{ item.name }}</h2>
					<text>{{ item.sex }}<text>|</text><text>{{ item.age }}</text></text>
					<u-icon v-if="selectedPatientIndex === index" name="checkbox-mark" class="checkmark" color="#0379ff"
						style="z-index: 999;"></u-icon>
				</view>
				<view class="add" @click="navigatoAddPatient">
					<u-icon name="plus" size="40px"></u-icon>
				</view>
			</view>
			<text style="color: darkgray;font-size: 18px;">是否有医保卡：</text>
			<view class="yibao" style="display: flex;">
				<button @click="toggleButtonStyle" :class="{ 'blue-background': isBlue }">是</button>
				<button @click="toggleButtonStyle" :class="{ 'blue-background': !isBlue }">否</button>
				<input type="number" placeholder="医保卡号" v-model="card">
				<button>确认就诊</button>
			</view>
			<text>就诊人手机：{{phone}}</text>
		</view>
		<button style="background-color: #0379ff;width: 400px;border-radius: 15px;color: aliceblue;" @click="submit">提交预约</button>
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
				type: "专家门诊",
				money: "318元",
				date: "5月5日",
				detailtime: "15:00-16:30",
				time: "2020年05月05日 周四下午",
				phone: "18791881394",
				isHave: false,
				card: "",
				patientList: [{
						name: "王戈",
						sex: '男',
						age: "30岁"
					},
					{
						name: "李静",
						sex: '女',
						age: "56岁"
					},
				],
				isBlue: false, // 新增一个用于切换按钮样式的状态
				selectedPatientIndex: -1, // 初始化为-1，表示没有选择任何患者
			};
		},
		methods: {
			navigatoAddPatient() {
				uni.navigateTo({
					url: '/pages/addPatient/addPatient'
				})
			},
			toggleButtonStyle() {
				this.isBlue = !this.isBlue; // 切换按钮样式状态
			},
			selectPatient(index) {
				// 切换选中状态
				this.selectedPatientIndex = this.selectedPatientIndex === index ? -1 : index;
			},
			
			submit(){
				//预约提交
				// uni.showModal({
				//     title: '提示',
				//     content: '预约成功!',
				//     success: function (res) {
				//         if (res.confirm) {
				//             console.log('用户点击确定');
				// 			uni.navigateTo({
				// 				url:'/pages/doorSuccess/doorSuccess'
				// 			})
				//         } else if (res.cancel) {
				//             console.log('用户点击取消');
				//         }
				//     }
				// });
				uni.request({
					url:'http://101.42.48.138:5000/reserve',
					method:'POST',
					header:{
						'token':''
					},
					success: (res) =>{
						console.log("预约",res);
						if(res.data.status == 'success'){
							console.log("进入");
							uni.showModal({
							    title: '提示',
							    content: '预约成功!',
							    success: function (res) {
							        if (res.confirm) {
							            console.log('用户点击确定');
										uni.navigateTo({
											url:'/pages/doorSuccess/doorSuccess'
										})
										// uni.navigateBack();
							        } else if (res.cancel) {
							            console.log('用户点击取消');
							        }
							    }
							});
						}
					}
				})
			}
		}
	}
</script>

<style lang="less">
	.container {
		background-color: #f6f8ff;

		.card-top {
			padding: 10px;
			margin: 30px;
			background-color: #fff;

			.doctor {
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

				}
			}
		}

		.card-bottom {
			margin-top: 20px;
			padding: 20px;
			margin: 20px;
			background-color: #fff;

			.selPatients {
				display: flex;
				margin-bottom: 10px;

				.patient {
					padding: 5px;
					margin-left: 20px;
					width: 150px;
					text-align: center;

					text {
						margin: 5px;
						color: #bbbcbe;
					}

				}

				.patient {
					border: 2px solid transparent;
					/* 初始边框样式为透明 */
					cursor: pointer;
					/* 鼠标指针样式为手型 */
					padding: 10px;
					/* 添加一些内边距 */
					position: relative;

					&:hover {
						border-color: #0379ff;
						/* 鼠标悬停时边框变蓝色 */
						border-radius: 10px;
					}

					&.selected {
						border-color: #0379ff;
						/* 选中时边框变蓝色 */
						border-radius: 10px;
					}

					.checkmark {
						position: absolute;
						bottom: 5px;
						right: 5px;
						color: #0379ff;
						 display: block; 
					}
				}

				.add {
					width: 150px;
					height: 70px;
					background-color: #fff;
					margin-left: 20px;
					display: flex;
					align-items: center;
					justify-content: center;
				}
			}

			.yibao {
				display: flex;
				align-items: center;
				margin-bottom: 40px;

				button {
					width: 80px;
				}

				input {
					width: 180px;
					height: 40px;
					border-bottom: 1px sold #0379ff;
				}

				button:active {
					background-color: #0379ff;
				}

				button.blue-background {
					background-color: #0379ff; // 设置按钮的蓝色背景样式
				}
			}
		}

	}
</style>