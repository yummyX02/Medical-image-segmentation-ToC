<template>
	<!-- 页面1 -->
	<view class="container">
		<view class="myNavbar">
			<view class="left">
				<u-icon name="arrow-left" size="28" @click="navigatoHome"></u-icon>
			</view>
			<view class="mid">
				<u-icon name="search" color="#ebebeb" size="28" @click="search"></u-icon>
				<u-input class="uinpt" placeholderStyle="font-size: 13px;" v-model="searchInfo" @confirm="onEnter"
					placeholder="搜索医院名称" />
			</view>
			<view class="right" @click="navigatoSelCity">
				<image src="../../static/icon-location.png" mode="" class="locationImg"></image>
				<text>{{city}}</text>
			</view>
		</view>
		<view class="selectBar">
			<view class="sel">综合排序<u-icon name="arrow-down-fill" size="12"></u-icon>
			</view>
				<view @click="navigatoOffice" class="box">科室<u-icon name="arrow-down-fill" size="12"></u-icon>
			</view>
			<view @click="navigatoFilter" class="box">筛选<u-icon name="arrow-down-fill" size="12"></u-icon>
			</view>
		</view>
		<u-popup :show="show" :round="10" mode="right" @close="close" @open="open">
			<view>
				
			</view>
		</u-popup>
		<view class="infoList" v-for="(item,index) in listData" :key="index">
			<view class="card" @click="onClick">
				<image :src="item.url" alt="Card Image" class="card-image" mode="aspectFit"></image>
				<view class="card-content">
					<text class="card-title">{{item.name}}</text>
					<view class="card-subtitle-text">
						<u-icon name="map-fill"></u-icon>
						<text class="card-text">
							{{item.location}}
						</text>
						<text class="card-subtitle">{{item.distance}}km</text>
					</view>
					<view class="tags">
						<uni-tag class="myTag" :circle="true" text="综合排名第一" type="primary" />
						<uni-tag class="myTag" :inverted="true" text="内科" />
						<uni-tag class="myTag" :inverted="true" text="口腔科" />
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				city: "天津",
				searchInfo: '',
				rules: '',
				office: "",
				show: false,
				range1: [{
						value: 0,
						text: "距离最近"
					},
					{
						value: 1,
						text: "排名最高"
					},
				],
				listData: [{
					url: "/static/doctor1.jpg",
					name: "北京协和医院",
					location: "北京市东城区东单北大街53号",
					distance: 2.5,

				}]
			};
		},
		methods: {
			search() {
				console.log(this.searchInfo);
				// 向后端发送查询
			},
			navigatoHome() {
				uni.reLaunch({
					url:'/pages/index/home'
				})
			},
			navigatoFilter() {
				uni.navigateTo({
					url: "/pages/filter/filter"
				})
			},
			navigatoOffice() {
				uni.navigateTo({
					url: "/pages/office/office"
				})
			},
			navigatoSelCity() {
				uni.navigateTo({
					url: "/pages/selCity/selCity"
				})
			},
			open() {
				this.show = true;
				// console.log('open');
			},
			close() {
				this.show = false
				// console.log('close');
			},
			onClick(){
				uni.navigateTo({
					url:'/pages/hospitalDetail/hospitalDetail'
				})
			}
		},
		onShow() {
			uni.getStorage({
				key:'city',
				success(res) {
					this.city = res.data;
				}
			})
		}
	}
</script>

<style lang="less">
	.container {
		background-color: #f6f7ff;

		.myNavbar {
			display: flex;
			flex-direction: row;
			justify-content: space-evenly;
			align-items: center;
			padding: 5px;
			box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.2);
			border-radius: 8px;
			margin-bottom: 5px;
			margin-top: 30px;

			.right {
				display: flex;
				flex-direction: row;
				align-items: center;

				.locationImg {
					width: 30px;
					height: 30px;
					margin-right: 5px;
				}

			}

			.mid {
				display: flex;
				border: 1px solid #ebebeb;
				border-radius: 5px;

				/deep/.uinpt {
					border: none;
				}

			}

			.left {
				.mesImg {
					width: 30px;
					height: 30px;
				}
			}
		}

		.selectBar {
			display: flex;
			align-items: center;
			justify-content: space-between;
			padding: 5px 15px 5px 15px;

			.sel {
				padding: 5px;
				padding: 5px;
				width: 120px;
				height: 35px;
				background-color: #fff;
				text-align: center;
				display: flex;
				justify-content: space-between;
			}

			.box {
				padding: 5px;
				width: 90px;
				height: 35px;
				background-color: #fff;
				margin-left: 20px;
				text-align: center;
				display: flex;
				justify-content: space-between;
				align-items: center;
			}
		}

	}

	.card {
		display: flex;
		align-items: center;
		justify-content: space-between;
		/* 将内容水平分散对齐 */
		border: 1px solid #ccc;
		border-radius: 5px;
		padding: 10px;
		margin: 15px;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);

		.card-image {
			max-width: 80px;
			height: 70px;
			margin-right: 10px;
		}

		.card-content {
			flex: 1;
			/* 占满剩余空间 */
		}

		.card-title {
			font-weight: bold;
			font-size: 18px;
		}

		.card-subtitle-text {
			display: flex;
			align-items: center;
			margin-top: 10px;
			color: #555;

		}

		.card-subtitle {
			color: #555;
			font-size: 14px;
			margin-left: 5px;
		}

		.card-text {
			margin-left: 5px;
			font-size: 14px;
			/* 增加一些间距 */
		}

		.tags {
			display: flex;

			.myTag {
				margin-right: 10px;
				margin-top: 15px;
			}
		}
	}
</style>