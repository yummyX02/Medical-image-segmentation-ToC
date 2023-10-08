<template>
	<view class="container">
		<view class="doctorList">
			<view class="tab-bar">
				<view class="baishe">
					不限<br>日期
				</view>
				<view v-for="(item, index) in guideList" :key="index" class="tab-item"
					:class="{ 'active-tab': currentIndex === index, 'inactive-tab': currentIndex !== index }"
					@tap="changeTab(index)">
					<view class="father">
						<view class="top">
							{{ item.name }}
						</view>
						<view class="bottom">
							<text v-if="item.status">
								当日有号
							</text>
							<text v-else style="color: red;">
								当日约满
							</text>
						</view>
					</view>
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
										<view class="btn">
											<text class="orderBtn" @click="navigatoHosList">预约挂号</text>
											<text class="consult">在线咨询</text>
										</view>
									</view>
								</view>
								<view class="right">
									<button class="smallOrder" @click="navigatoHosList">预约</button>
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
				list: [{
						src: "../../static/banner1.png"
					},
					{
						src: "../../static/banner2.png"
					},
					{
						src: "../../static/banner3.png"
					},
				],
				guideList: [{
						name: "5.18",
						status:true
					},
					{
						name: "5.19",
						status:true
						
					},
					{
						name: "5.20",
						status:true
					},
					{
						name: "5.21",
						status:false
					},
					{
						name: "5.22",
						status:true
					},
					{
						name: "5.23",
						status:true
					},
					{
						name: "5.24",
						status:true
					}
				],
				tabs: [{
						name: '严选专家',
						index: 0,
					},
					{
						name: '口腔专家',
						index: 1,
					},
					{
						name: '骨科专家',
						index: 2,
					},
					{
						name: '妇科专家',
						index: 3,
					},
					{
						name: '儿童专家',
						index: 4,
					}
				],
				listData: [
					[{
							id: 1,
							headUrl: '/static/doctor1.jpg',
							name: "王医生",
							identify: "主任医师",
							hospital: "天津中医药大学一附属医院 ",
							office: "心血管科",
							advantage: "擅长：心血管疾病、心脏病、冠心病",

						},
						{
							id: 2,
							headUrl: '/static/doctor1.jpg',
							name: "王医生",
							identify: "主任医师",
							hospital: "天津中医药大学一附属医院 ",
							office: "心血管科",
							advantage: "擅长：心血管疾病、心脏病、冠心病",

						},
						{
							id: 3,
							headUrl: '/static/doctor1.jpg',
							name: "王医生",
							identify: "主任医师",
							hospital: "天津中医药大学一附属医院 ",
							office: "心血管科",
							advantage: "擅长：心血管疾病、心脏病、冠心病",

						}
					],
					[{
							id: 4,
							headUrl: '/static/doctor1.jpg',
							name: "王医生",
							identify: "主任医师",
							hospital: "天津中医药大学一附属医院 ",
							office: "心血管科",
							advantage: "擅长：心血管疾病、心脏病、冠心病",

						},
						{
							id: 5,
							headUrl: '/static/doctor1.jpg',
							name: "王医生",
							identify: "主任医师",
							hospital: "天津中医药大学一附属医院 ",
							office: "心血管科",
							advantage: "擅长：心血管疾病、心脏病、冠心病",

						}
					],
					[{
							id: 6,
							headUrl: '/static/doctor1.jpg',
							name: "王医生",
							identify: "主任医师",
							hospital: "天津中医药大学一附属医院 ",
							office: "心血管科",
							advantage: "擅长：心血管疾病、心脏病、冠心病",

						},
						{
							id: 7,
							headUrl: '/static/doctor1.jpg',
							name: "王医生",
							identify: "主任医师",
							hospital: "天津中医药大学一附属医院 ",
							office: "心血管科",
							advantage: "擅长：心血管疾病、心脏病、冠心病",

						}
					]
				]
			}
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
			changeTab(index) {
				// 切换标签时更新currentIndex
				this.currentIndex = index;
			},
			swiperChange(e) {
				// 轮播图切换时更新currentIndex
				this.currentIndex = e.detail.current;
			},
			navigatoHosList(){
				uni.navigateTo({
					url:'/pages/internetDoctor/internetDoctor'
				})
			}
		}
	}
</script>

<style lang="less" scoped>
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
			.baishe{
				margin-left:5px;
				border-bottom: 4px solid #0379ff;
			}
			.father{
				display: flex;
				flex-direction: column;
				align-items: center;
				.top{
					
				}
				.bottom{
					color: #ffb563;
					font-size: 14px;
				}
			}

			/* 防止标签换行 */
			.tab-item {
				padding: 5px 1px 5px 10px;
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