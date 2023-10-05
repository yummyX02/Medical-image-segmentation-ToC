
<template>
	<view class="container">
		<view class="card-list">
			<scroll-view class="newlist" :scroll-y="true">
				<!-- 在这里放置列表内容 -->
				<view v-for="(item,index) in yuyueList" :key="index" class="list-item uni-bg-red">
					<view class="top">
						<view class="btn">
							<text class="consult" style="font-size: 14px; ">{{item.patient}}<text
									style="margin-left: 5px;">{{item.sex}}</text></text></text>
						</view>
						<view class="right">
							<u-icon name="edit-pen-fill" size="28" @click="navigatoXiugai(index)"></u-icon>
						</view>
					</view>
					<view class="mid">
						<text style="color: darkgray; font-size:14px;">身份证：</text>
						<text class="hospital">{{item.grade}}<text class="office">{{item.identify}}</text></text>
					</view>
					<view class="mid">
						<text style="color: darkgray; font-size:14px;">手机号码：</text>
						<text class="hospital">{{item.grade}}<text class="office">{{item.phone}}</text></text>
					</view>

				</view>
			</scroll-view>
		</view>
		<view class="footer">
			<text>您还能添加<text class="special">{{number}}</text>名就诊人</text>
			<button @click="navigatoAdd">添加就诊人</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				yuyueList: [{
						id: 1,
						identify: "360302********1234",
						phone: "15812345678",
						patient: "张女士",
						sex: "男",
						age: "30岁"
					},
					{
						id: 2,
						identify: "360302********1234",
						phone: "15812345678",
						patient: "张女士",
						sex: "男",
						age: "30岁"
					},
					{
						id: 3,
						identify: "360302********1234",
						phone: "15812345678",
						patient: "张女士",
						sex: "男",
						age: "30岁"
					}
				],
				number: 1,
			};
		},
		mounted() {
			this.number = this.yuyueList.length;
		},
		methods:{
			navigatoXiugai(index){
				const info = this.yuyueList[index];
				uni.navigateTo({
					url:"/pages/xiugaiPatient/xiugaiPatient",
					success: res => {
						uni.setStorage({
							key: 'patientInfo',
							data: info,
							success: function () {
								console.log('success',info);
							}
						});
					},
				})
			},
			navigatoAdd(){
				uni.navigateTo({
					url: '/pages/addPatient/addPatient',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		}
	}
</script>

<style lang="less" scoped>
	.container {
		background-color: #f7f8ff;
		height: 90vh;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		/* 垂直方向上平均分布，将顶部和底部内容分开 */

		.newlist {
			height: 100%;

			/* 设置列表高度，根据需求调整 */
			.list-item {
				padding: 10px;
				border-bottom: 1px solid #ccc;
				box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.2);
				margin: 15px 25px 10px 25px;
				border-radius: 10px;

				.top {
					display: flex;
					justify-content: space-between;
					margin-left: 10px;
				}

				.leftImg {
					width: 90px;
					height: 90px;
				}

				.mid {
					margin-left: 10px;
					display: flex;
					align-items: center;

					h4 {
						display: flex;
						margin-right: 5px;
					}

					h5 {
						padding-left: 5px;
					}

					.hospital {
						display: flex;
						font-size: 14px;
						margin-top: 5px;

						.office {
							margin-left: 5px;
						}
					}

					.great {
						color: #ccc;
						font-size: 14px;
						margin-top: 5px;
					}

					.btn {
						display: flex;
						color: #0379ff;
						font-size: 14px;
						margin-top: 5px;

						.orderBtn {}

						.consult {
							margin-left: 5px;
						}
					}

				}

				.right {
					margin-left: 20px;

					.smallOrder {
						display: flex;
						align-items: center;
						color: #0379ff;
						background-color: #fff;
						width: 70px;
						height: 25px;
						font-size: 14px;
						border-radius: 30px;
						border: none;
					}
				}
			}
		}

		.footer {
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;

			button {
				background-color: #0379ff;
				width: 70%;
				border-radius: 25px;
				color: #fff;
				margin-top: 10px;
			}

			text {
				color: darkgray;
			}

			.special {
				color: #ffa926;
			}
		}
	}
</style>