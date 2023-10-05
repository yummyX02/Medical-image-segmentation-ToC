<template>
	<view class="personal-center">
		<!-- 头部 -->
		<div class="header">
			<div class="user-info">
				<image class="avatar" :src="user.headUrl" alt="User Avatar" />
				<!-- 管理信息按钮 -->
				<div class="manage-info">
					<p class="phone-number">{{ user.phoneNumber }}</p>
					<u-button text="管理信息" class="mybn"></u-button>
				</div>
			</div>
			<div class="icons">
				<u-icon class="myicon" color="black" name="setting-fill" size="28" @click="goToSettings"></u-icon>
				<u-icon class="myicon" color="black" name="server-fill" size="28" @click="openCustomerService"></u-icon>
			</div>
		</div>
		<!-- 我的预约卡片 -->
		<div class="appointment-card">
			<h3>我的预约</h3>
			<div class="appointment-buttons">
				<view class="jiuzhen" @click="navigatoJiuzhen">
					<image class="myimg" src="../../static/icon-daijiuzhen.png" mode=""></image>
					<view class="badge">
						<text class="badge-text">7</text>
					</view>
					<text>待就诊</text>
				</view>
				<view class="jiuzhen">
					<image class="myimg" src="../../static/ic-yijiuzhen.png" mode=""></image>
					<view class="badge">
						<text class="badge-text">7</text>
					</view>
					<text>已就诊</text>
				</view>
				<view class="jiuzhen">
					<image class="myimg" src="../../static/icon-lishi.png" mode=""></image>
					<view class="badge">
						<text class="badge-text">7</text>
					</view>
					<text>历史</text>
				</view>
			</div>
		</div>

		<!-- 底部列表 -->
		<div class="bottom-list">
			<u-list>
				<u-list-item >
					<u-cell title="我的就诊人" @click="navigatoguanli">
						<u-avatar slot="icon" shape="square" size="35" src="../../static/icon-wodejiuzhenren.png"
							customStyle="margin: -3px 5px -3px 0"></u-avatar>
					</u-cell>
				</u-list-item>
				<u-list-item>
					<u-cell title="我的咨询"  @click ="navigatoZixun">
						<u-avatar slot="icon" shape="square" size="35" src="../../static/icon-zixun.png"
							customStyle="margin: -3px 5px -3px 0"></u-avatar>
					</u-cell>
				</u-list-item>
				<u-list-item>
					<u-cell title="我的收藏">
						<u-avatar slot="icon" shape="square" size="35" src="../../static/icon-wodeshoucang.png"
							customStyle="margin: -3px 5px -3px 0"></u-avatar>
					</u-cell>
				</u-list-item>
				<u-list-item>
					<u-cell title="帮助中心">
						<u-avatar slot="icon" shape="square" size="35" src="../../static/icon-bangzhu.png"
							customStyle="margin: -3px 5px -3px 0"></u-avatar>
					</u-cell>
				</u-list-item>
			</u-list>
		</div>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				user: {
					headUrl: "/static/icon-me-no.png",
					phoneNumber: "123-456-7890",
				}
			};
		},
		methods: {
			goToSettings() {
				// 导航到设置页面
			},
			openCustomerService() {
				// 打开客服界面
			},
			manageInfo() {
				// 管理信息操作
			},
			viewAppointments(status) {
				// 根据状态查看预约
			},
			viewPatientInfo() {
				// 查看就诊人信息
			},
			viewConsultations() {
				// 查看咨询信息
			},
			viewFavorites() {
				// 查看收藏内容
			},
			openHelpCenter() {
				// 打开帮助中心
			},
			navigatoJiuzhen(){
				uni.navigateTo({
					url:"/pages/yuyue/yuyue"
				})
			},
			navigatoZixun(){
				uni.navigateTo({
					url:"/pages/zixun/zixun"
				})
			},
			navigatoguanli(){
				uni.navigateTo({
					url:"/pages/patientManage/patientManage"
				})
			},
			goToSettings(){
				uni.navigateTo({
					url:'/pages/settinfs/settinfs'
				})
			}
		},
	};
</script>

<style lang="less" scoped>
	/* 样式可以根据你的设计进行定制 */
	.personal-center {
		/* 页面样式 */
		background-color: #f7f8ff;
		.header {
				/* 头部样式 */
				padding: 10px;
				height: 200px;
				background-color: #0379ff;
				display: flex;
				align-items: center;
				justify-content: space-between;
		
				.user-info {
					/* 用户信息样式 */
					display: flex;
					flex-direction: row;
					align-items: center;
				}
		
				.avatar {
					/* 头像样式 */
					width: 35px;
					height: 35px;
					border-radius: 50%;
					background-color: #fff;
					padding: 5px;
					margin-right: 9px;
				}
		
				.manage-info p,
				.manage-info u-button {
					text-align: left;
				}
		
				.phone-number {
					/* 手机号样式 */
					font-size: 20px;
					font-weight: bold;
				}
		
				.icons {
					/* 图标样式 */
					display: flex;
		
				}
		
				.myicon {
					margin-right: 15px;
				}
		
				.mybn {
					height: 23px;
					width: 65px;
					font-size: 8px;
					text-align: center;
					display: flex;
					border-radius: 10px;
					background-color: #065bbc;
					color: #fff;
					border: none;
				}
		
		
		
			}
		
			.appointment-card {
				/* 预约卡片样式 */
				display: flex;
				flex-direction: column;
				text-align: left;
				/* 将内容水平分散对齐 */
				border: 1px solid #ccc;
				border-radius: 5px;
				padding: 10px;
				margin: 10px;
				box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
				margin: 20px 30px 5px 30px;
			}
		
			.appointment-buttons {
				/* 预约按钮样式 */
				display: flex;
				justify-content: space-between;
				width: 100%;
		
				.myimg {
					text-align: center;
					width: 50px;
					height: 50px;
				}
		
				.jiuzhen {
					display: flex;
					flex-direction: column;
					align-items: center;
					color: #ccc;
					padding: 15px;
				}
			}
		
			.bottom-list {
				/* 底部列表样式 */
				/* 预约卡片样式 */
				display: flex;
				flex-direction: column;
				text-align: left;
				/* 将内容水平分散对齐 */
				border: 1px solid #ccc;
				border-radius: 5px;
				padding: 20px;
				margin: 10px;
				box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
				height: 250px;
				margin: 20px 30px 5px 30px;
			}
		
			.list-item {
				/* 列表项样式 */
			}
		.badge {
		    position: relative;
		    display: inline-block;
		    margin-left: 5px;
		}
		
		.badge-text {
		    background-color: red;
		    color: white;
		    font-size: 12px;
		    border-radius: 50%;
		    padding: 2px 6px;
		    position: absolute;
		    top: -45px;
		    right: -25px;
		    transform: translate(50%, -50%);
		}
	}

	
</style>