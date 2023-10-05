<template>
	<view class="container">
		<topBar></topBar>
		<view class="doctorList">
			<view class="tab-bar">
				<view v-for="(item, index) in guideList" :key="index" class="tab-item"
					:class="{ 'active-tab': currentIndex === index, 'inactive-tab': currentIndex !== index }"
					@tap="changeTab(index)">
					{{ item.name }}
				</view>
			</view>

			<view class="swiperList">
				<!-- 轮播列表 -->
				<swiper class="newSwiper" :duration="300" :current="currentIndex" @change="swiperChange">
					<swiper-item v-for="(tab,index) in tabs" :key="index">
						<!-- 对应的列表 -->
						<scroll-view class="newlist" :scroll-y="true">
							<!-- 在这里放置列表内容 -->
							<view v-for="item in listData[index]" :key="item.id" class="list-item uni-bg-red">
								<view class="mid">
									<view class="leftInfo">
										<h4>{{item.title}}
										</h4>
										<text class="hospital">{{item.describe}}</text>
										<view class="btn">
											<text class="hospital">{{item.num}}阅读</text>
											<text class="hospital">{{item.date}}</text>
										</view>
									</view>
								</view>
								<view class="left">
									<image class="leftImg" :src="item.headUrl" mode=""></image>
								</view>

							</view>
						</scroll-view>
					</swiper-item>

				</swiper>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				currentIndex: 0,
				swiperCurrent: 0,
				tabs: [{
						name: '我关注的',
						index: 0,
					},
					{
						name: '心理测试',
						index: 1,
					},
					{
						name: '健康养生',
						index: 2,
					},
					{
						name: '医疗动态',
						index: 3,
					},
					{
						name: '育儿专刊',
						index: 4,
					}
				],
				guideList: [{
						name: "我关注的"
					},
					{
						name: "心理测试"
					},
					{
						name: "健康养生"
					},
					{
						name: "医疗动态"
					},
					{
						name: "育儿专刊"
					}
				],
				listData: [
					[{
							id: 1,
							headUrl: '/static/doctor1.jpg',
							title: "空腹能不能吃汤圆?无糖汤圆不“ 胖人” 吗 ?",
							describe:"元宵吃汤圆，有什么禁忌吗?",
							num:8908,
							date:"2023-09-30",

						},
						{
							id: 2,
							headUrl: '/static/doctor1.jpg',
							headUrl: '/static/doctor1.jpg',
							title: "空腹能不能吃汤圆?无糖汤圆不“ 胖人” 吗 ?",
							describe:"元宵吃汤圆，有什么禁忌吗?",
							num:8908,
							date:"2023-09-30",

						},
						{
							id: 3,
							headUrl: '/static/doctor1.jpg',
							title: "空腹能不能吃汤圆?无糖汤圆不“ 胖人” 吗 ?",
							describe:"元宵吃汤圆，有什么禁忌吗?",
							num:8908,
							date:"2023-09-30",

						}
					],
					[{
							id: 4,
							headUrl: '/static/doctor1.jpg',
							title: "空腹能不能吃汤圆?无糖汤圆不“ 胖人” 吗 ?",
							describe:"元宵吃汤圆，有什么禁忌吗?",
							num:8908,
							date:"2023-09-30",
						},
						{
							id: 5,
							headUrl: '/static/doctor1.jpg',
							title: "空腹能不能吃汤圆?无糖汤圆不“ 胖人” 吗 ?",
							describe:"元宵吃汤圆，有什么禁忌吗?",
							num:8908,
							date:"2023-09-30",

						}
					],
					[{
							id: 6,
							headUrl: '/static/doctor1.jpg',
							title: "空腹能不能吃汤圆?无糖汤圆不“ 胖人” 吗 ?",
							describe:"元宵吃汤圆，有什么禁忌吗?",
							num:8908,
							date:"2023-09-30",

						},
						{
							id: 7,
							headUrl: '/static/doctor1.jpg',
							title: "空腹能不能吃汤圆?无糖汤圆不“ 胖人” 吗 ?",
							describe:"元宵吃汤圆，有什么禁忌吗?",
							num:8908,
							date:"2023-09-30",

						}
					]
				]
			};
		},
		methods: {
			// tabs通知swiper切换
			tabsChange(index) {
				this.swiperCurrent = index;
			},
			// swiper-item左右移动，通知tabs的滑块跟随移动
			transition(e) {
				let dx = e.detail.dx;
				this.$refs.tabs.setDx(dx);
			},
			// 由于swiper的内部机制问题，快速切换swiper不会触发dx的连续变化，需要在结束时重置状态
			// swiper滑动结束，分别设置tabs和swiper的状态
			animationfinish(e) {
				let current = e.detail.current;
				this.$refs.tabs.setFinishCurrent(current);
				this.swiperCurrent = current;
				this.current = current;
			},
			// scroll-view到底部加载更多
			onreachBottom() {

			},
			changeTab(index) {
				// 切换标签时更新currentIndex
				this.currentIndex = index;
			},
			swiperChange(e) {
				// 轮播图切换时更新currentIndex
				this.currentIndex = e.detail.current;
			},
		}
	}
</script>

<style lang="less">
	.container {


		.tab-bar {
			display: flex;
			justify-content: space-between;
			/* 横向排列 */
			align-items: center;
			/* 垂直居中 */
			padding: 5px 0;
			overflow-x: scroll;
			/* 添加横向滚动条 */
			white-space: nowrap;

			/* 防止标签换行 */
			.tab-item {
				padding: 5px 15px 5px 15px;
				font-size: 16px;
				color: gray;
				/* 设置默认颜色为灰色 */
				display: flex;
			}

			.active-tab {
				font-weight: bold;
				font-size: 20px;
				color: black;
				/* 设置活动标签颜色为黑色 */
			}

			.inactive-tab {
				color: gray;
				/* 设置非活动标签颜色为灰色 */
			}

			.tab-text {
				font-size: 16px;
			}
		}

		.swiperList {
			height: 500px;
			margin-top: 8px;
			background-color: #ffffff;

			.newSwiper {
				height: 100%;

				.newlist {
					height: 100%;

					/* 设置列表高度，根据需求调整 */
					.list-item {
						padding: 10px;
						border-bottom: 1px solid #ccc;
						display: flex;
						box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.2);
						margin: 0 15px 5px 15px;

						.leftImg {
							width: 100px;
							height: 100px;
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
								margin-top: 15px;

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
								color: #d9d9d9;
								font-size: 14px;
								margin-top: 10px;
								justify-content: space-between;

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
								background-color: #0379ff;
								color: #fff;
								width: 60px;
								height: 25px;
								font-size: 14px;
								border-radius: 30px;
							}
						}
					}
				}
			}
		}
	}
</style>