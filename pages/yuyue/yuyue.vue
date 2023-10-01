<template>
	<view class="container">
		<view class="card-list">
			<scroll-view class="newlist" :scroll-y="true">
				<!-- 在这里放置列表内容 -->
				<view v-for="(item,index) in yuyueList" :key="index" class="list-item uni-bg-red">
					<view class="top">
						<view class="left">
							<image class="leftImg" :src="item.headUrl" mode=""></image>
						</view>
						<view class="mid">
							<view class="leftInfo">
								<h4>{{item.name}}
									<h5>{{item.identify}}</h5>
								</h4>
								<text class="hospital">{{item.hospital}}<text
										class="office">{{item.office}}</text></text>
								<text class="great">{{item.advantage}}</text>

							</view>
						</view>
						<view class="right">
							<button class="smallOrder" @click="navigatoHosList">待就诊</button>
						</view>
					</view>
					<view class="btn">
						<text class="orderBtn"style="margin-left: 10px; font-size: 14px; color: #dcd5d2;">就诊人：</text>
						<text class="consult" style="font-size: 14px; ">{{item.patient}}<text style="margin-left: 5px;">{{item.date}}</text><text style="margin-left: 5px;">{{item.time}}</text></text></text>
					</view>
				</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				yuyueList: [{
						id: 1,
						headUrl: '/static/doctor1.jpg',
						name: "王医生",
						identify: "主任医师",
						hospital: "天津中医药大学一附属医院 ",
						office: "心血管科",
						advantage: "擅长：心血管疾病、心脏病、冠心病",
						patient: "张女士",
						date: "2023-05-09",
						time: "上午"
					},
					{
						id: 2,
						headUrl: '/static/doctor1.jpg',
						name: "王医生",
						identify: "主任医师",
						hospital: "天津中医药大学一附属医院 ",
						office: "心血管科",
						advantage: "擅长：心血管疾病、心脏病、冠心病",
						patient: "张女士",
						date: "2023-05-09",
						time: "上午"

					},
					{
						id: 3,
						headUrl: '/static/doctor1.jpg',
						name: "王医生",
						identify: "主任医师",
						hospital: "天津中医药大学一附属医院 ",
						office: "心血管科",
						advantage: "擅长：心血管疾病、心脏病、冠心病",
						patient: "张女士",
						date: "2023-05-09",
						time: "上午"

					}
				]
			};
		}
	}
</script>

<style lang="less">
	.container {
		background-color: #f7f8ff;
		height: 100%;
		.newlist {
			height: 100%;
			margin-top: 15px;

			/* 设置列表高度，根据需求调整 */
			.list-item {
				padding: 10px;
				border-bottom: 1px solid #ccc;
				box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.2);
				margin: 0 15px 5px 15px;

				.top {
					display: flex;
				}

				.leftImg {
					width: 90px;
					height: 90px;
				}

				.mid {
					margin-left: 10px;

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

	}
</style>