<template>
	<view>
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
		<view class="mid">
			<view @click="navigatoInternet" class="btn" style="background-color: #f9e8cd;margin-right: 20px;">
				<u-icon name="order" color="#ffa903" size="28"></u-icon>
				<text>互联网预约</text>
			</view>
			<view @click="navigatoDoor"  class="btn" style="background-color: #c0d6f4;margin-right: 20px;">
				<u-icon name="list-dot" color="#2979ff" size="28"></u-icon>
				<text>门诊挂号</text>
			</view>
			<view class="btn" style="background-color: #c7f9eb;">
				<u-icon name="chat" color="#07ff9e" size="28"></u-icon>
				<text>智能导诊</text>
			</view>
		</view>
		<view class="bottom">
			<view class="card" style="display: flex;flex-direction: column;text-align: left;">
				<h2>医院简介</h2>
				<p style="color: darkgray;">
					北京协和医院是一-所位于北京市东城区，集医疗、
					科研、教学为- -体的大型综合医院。它隶属于中国
					协和医科大学(2006年改为北京协和医学院/清华大
					学医学部)，是其临床医学院，同时也是中国医学科
					学院的临床医学研究所，中华人民共和国卫生部指
					定的诊治疑难重症的技术指导中心之一。北京协和
					医院在中国乃至世界享有盛名。医院成立于1921
					年。现任院长赵玉沛。北京协和医院是中国最早承
					担外宾医疗任务的单位，医院专门设立外宾和高干
					门诊部，开设专门的高干、外宾、特需病区。2006
					年7月28日被中国奥委会定为“国家队运动员医疗服
					务指定医院”。

				</p>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				item: {
					url: "/static/doctor1.jpg",
					name: "北京协和医院",
					location: "北京市东城区东单北大街53号",
					distance: 2.5,

				}
			};
		},
		methods:{
			navigatoInternet(){
				uni.navigateTo({
					url:'/pages/internetOrder/internetOrder'
				})
			},
			navigatoDoor(){
				uni.navigateTo({
					url:'/pages/doorOrder/doorOrder'
				})
			},
		}
	}
</script>

<style lang="less">
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
	.mid{
		display: flex;
		justify-content: center;
		align-items: center;
		.btn{
			padding: 20px;
			display: flex;
			flex-direction: column;
			align-items: center;
			border: none;
			border-radius: 100%;
			text{
				margin-top: 10px;
			}
		}
	}
</style>