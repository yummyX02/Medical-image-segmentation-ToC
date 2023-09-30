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
			<view class="right">
				<image src="../../static/icon-location.png" mode="" class="locationImg"></image>
				<text>{{city}}</text>
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
			};
		},
		methods:{
			search() {
				console.log(this.searchInfo);
				// 向后端发送查询
			},
			navigatoHome(){
				uni.reLaunch({
					url:"/pages/index/home"
				})
			}
		}
	}
</script>

<style lang="less">
	.container {
		.myNavbar {
			display: flex;
			flex-direction: row;
			justify-content: space-evenly;
			align-items: center;
			padding: 5px;
			box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.2);
			border-radius: 8px;

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
	}
</style>