<template>
	<view class="container">
		<topBar></topBar>

		<div class="myswiper">
			<swiper class="swiper" :indicator-dots="true">
				<swiper-item class="item" v-for="(item, index) in list" :key="index">
					<image :src="item.src" class="image-container"></image>
				</swiper-item>
			</swiper>
		</div>
		<div class="guider">
			<div class="order" @click="navigatoHosList">
				<div class="left">
					<h2>预约挂号</h2>
					<h5>全国<h4 class="number">400+</h4>家医院</h5>
					<div class="internet">
						<image src="../../static/icon-fire.png"></image>
						<h4>互联网医院</h4>
					</div>
				</div>
				<div class="right">
					<image src="../../static/icon-enter.png" class="enterImg"></image>
				</div>
			</div>
			<div class="inquiry" @click="navigatoConslt">
				<div class="left">
					<h2>在线问诊</h2>
					<h5>知名专家，<h4 class="minute">5分钟</h4>回复</h5>
					<div class="speed">
						<image src="../../static/icon-speed.png"></image>
						<h4>急速</h4>
					</div>
				</div>
				<div class="right">
					<image src="../../static/icon-enter.png" class="enterImg"></image>
				</div>
			</div>
		</div>
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
						name: "严选专家"
					},
					{
						name: "口腔专家"
					},
					{
						name: "骨科专家"
					},
					{
						name: "妇科专家"
					},
					{
						name: "儿童专家"
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
							name: "王法医生",
							identify: "主任医师",
							hospital: "天津中医药大学一附属医院 ",
							office: "内科",
							advantage: "擅长：内分泌疾病",

						},
						{
							id: 2,
							headUrl: '/static/doctor2.png',
							name: "毕单医生",
							identify: "主任医师",
							hospital: "天津中医药大学一附属医院 ",
							office: "脑科",
							advantage: "擅长：脑部疾病",

						},
						{
							id: 3,
							headUrl: '/static/doctor3.png',
							name: "常明医生",
							identify: "副主任医师",
							hospital: "天津中医药大学一附属医院 ",
							office: "心血管科",
							advantage: "擅长：心脏病、冠心病",

						}
					],
					[{
							id: 4,
							headUrl: '/static/doctor4.png',
							name: "牛波医生",
							identify: "主任医师",
							hospital: "天津中医药大学一附属医院 ",
							office: "心血管科",
							advantage: "擅长：心血管疾病",

						},
						{
							id: 5,
							headUrl: '/static/doctor5.png',
							name: "董真医生",
							identify: "主任医师",
							hospital: "天津中医药大学一附属医院 ",
							office: "心血管科",
							advantage: "擅长：心血管疾病、心脏病、冠心病",

						}
					],
					[{
							id: 6,
							headUrl: '/static/doctor6.png',
							name: "王里医生",
							identify: "主任医师",
							hospital: "天津中医药大学一附属医院 ",
							office: "心血管科",
							advantage: "擅长：心血管疾病、心脏病、冠心病",

						},
						{
							id: 7,
							headUrl: '/static/doctor7.png',
							name: "明阿医生",
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
			navigatoHosList() {
				console.log("前往预约挂号");
				uni.reLaunch({
					url: "/pages/hospitalList/hospitalList"
				})
			},
			navigatoConslt() {
				console.log("前往在线问诊");
			},
			open() {
				// 通过组件定义的ref调用uni-popup方法 ,如果传入参数 ，type 属性将失效 ，仅支持 ['top','left','bottom','right','center']
				this.$refs.popup.open('center')
			}

		},
		onLoad() {
			let token = '';
			uni.switchTab({
			 			url: '/pages/index/home',
			});
			// uni.getStorage({
			// 	key: "access_token",
			// 	success: function(res) {
			// 		console.log("请求成功", res);
			// 		token = res.data;
			// 	},
			// 	fail: function(err) {
			// 		console.log(err);
			// 		token = err.data;
			// 	}
			// })
			// if (token) { //有token
			// 	console.log("有token");
			// 	setTimeout(function() {
			// 		uni.switchTab({
			// 			url: '/pages/index/home',
			// 		});
			// 	}, 100)
			// } else {
			// 	console.log("没有token，即将跳转登录页");
			// 	setTimeout(function() { //去登录
			// 		uni.reLaunch({
			// 			url: '/pages/login/login',
			// 		});
			// 	}, 100)
			// }
		}
	}
</script>

<style lang="less" scoped>
	.container {
		background-color: #f6f7ff;
		height: 100vh;

		.myswiper {
			width: 95vw;
			height: auto;
			padding: 5px;
			margin: 10px;

			.item {
				display: flex;
				width: 100%;
				width: 100%;
				border-radius: 15px;

			}

			.image-container {
				width: 100%;
				height: auto;
			}
		}

		.guider {
			background-color: #ffffff;
			margin: 10px;
			padding: 5px;
			display: flex;
			justify-content: space-between;
			align-items: center;

			.order {
				width: 47vw;
				margin-right: 2vw;
				height: 14vh;
				padding: 3px;
				display: flex;
				justify-content: space-between;
				background-color: #ffffff;
				border-radius: 8px;
				background: url(/static/bgc-hospital.png) no-repeat right;
				background-size: 80px 90px;
				box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.2);

				.internet {
					background-color: #ff932f;
					display: flex;
					align-items: center;
					width: 100%;
					border-radius: 20px;

					image {
						width: 18px;
						height: 18px;
						margin-left: 2px;
					}

					h4 {
						color: #fff;
					}
				}
			}

			.inquiry {
				width: 47vw;
				margin-left: 2vw;
				height: 14vh;
				padding: 3px;
				display: flex;
				justify-content: space-between;
				background-color: #ffffff;
				border-radius: 8px;
				background: url(/static/bgc-doctor.png) no-repeat right;
				background-size: 80px 90px;
				box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.2);

				.speed {
					background-color: #0379ff;
					display: flex;
					align-items: center;
					width: 50%;
					border-radius: 20px;

					image {
						width: 18px;
						height: 18px;
						margin-left: 2px;
					}

					h4 {
						color: #fff;
						border-radius: 10%;
					}
				}
			}

			.left {
				h5 {
					display: flex;
					align-items: center;
					font-size: 15px;
					color: #beb0a6;
					margin-bottom: 10px;

					.number {
						color: #ff932f;
					}

					.minute {
						color: #0379ff;
					}
				}

			}

			.right {
				.enterImg {
					width: 20px;
					height: 20px;
					margin-top: 8px;
				}
			}
		}

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