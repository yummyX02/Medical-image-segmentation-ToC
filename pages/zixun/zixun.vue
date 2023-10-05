<template>
	<view class="container">
		<view class="card-list">
			<scroll-view class="newlist" :scroll-y="true">
				<!-- 在这里放置列表内容 -->
				<view v-for="(item,index) in yuyueList" :key="index" class="list-item uni-bg-red">
					<view class="top">
						<view class="btn">
							<text class="consult" style="font-size: 14px; ">{{item.patient}}<text
									style="margin-left: 5px;">{{item.sex}}</text><text
									style="margin-left: 5px;">{{item.age}}</text></text></text>
						</view>
						<view class="right">
							<button class="smallOrder" @click="navigato">咨询中</button>
						</view>
					</view>
					<view class="mid">
							<text style="color: darkgray;font-size: 14px;">咨询医生：</text>
							<text class="hospital">{{item.grade}}<text class="office">{{item.hospital}}</text></text>
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
						identify: "主任医师",
						hospital: "天津中医药大学一附属医院 ",
						grade: "主任医师",
						patient: "张女士",
						sex: "男",
						age: "30岁"
					},
					{
						id: 2,
						grade: "主任医师",
						hospital: "天津中医药大学一附属医院 ",
						patient: "张女士",
						sex: "男",
						age: "30岁"
					},
					{
						id: 3,
						grade: "主任医师",
						hospital: "天津中医药大学一附属医院 ",
						patient: "张女士",
						sex: "男",
						age: "30岁"
					}
				]
			};
		}
	}
</script>

<style lang="less" scoped>
	.container {
		background-color: #f7f8ff;
		height: 100%;

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
					margin-top: 5px;

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