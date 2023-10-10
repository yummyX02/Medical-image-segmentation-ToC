<template>
	<view id="guide">
		<swiper class="swiper" circular :indicator-dots="true" :current="tabIndex" @change="changeTab">
			<swiper-item class="item" v-for="(item, index) in guidelList" :key="index">
				<text class="swiperImageName">{{item.name}}</text>
				<image :src="item.src" mode="aspectFill" class="image-container"></image>
				<view class="skip-button" @click="skipGuide">跳过</view>
				<view class="image-container start-button" v-if="index === guidelList.length - 1" @click="skipGuide">
					开始
				</view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tabIndex: 0,
				guidelList: [{
						name: '医学宣传',
						src: "../../static/swiper-spread.png"
					},
					{
						name: '线上问诊',
						src: "../../static/swiper-wenzhen.png"
					}, {
						name: '报告分析',
						src: "../../static/swiper-search.png"
					},
				],
				token:'',
			}
		},
		methods: {
			changeTab(e) {
				this.tabIndex = e.detail.current;
			},
			skipGuide() {
				console.log("可以跳转");
				//判断token
				
				uni.getStorage({
								key:"access_token",
								success: function (res) {
										console.log("请求成功",res);
									 token = res.data;
									},
								fail:function(err){
									console.log(err);
									 token = err.data;
								}
							})
				
				if(token){
					uni.switchTab({
						url:'/pages/login/login'
					})
				}else{
						uni.switchTab({
							url: '/pages/index/home'
						})
				}
				
			},
		}
	}
</script>

<style lang="less">
	#guide {

		.swiper {
			width: 100vw;
			height: 100vh;

			.item {
				display: flex;
				flex-direction: column;
				align-items: center;
				justify-content: center;

				.skip-button {
					position: absolute;
					top: 50px;
					right: 20px;
					padding: 10px 20px;
					background-color: rgba(0, 0, 0, 0.5);
					color: #fff;
					border-radius: 5px;
					cursor: pointer;
				}

				.start-button {
					background-color: #068cff;
					color: #fff;
					width: 60vw;
					height: 5vh;
					border-radius: 10px;
					display: flex;
					justify-content: center;
					align-items: center;
				}

				.image-container image {
					width: 100%;
					height: 100%;
					display: block;
				}

				.swiperImageName {
					font-size: 30px;
					color: black;
					font-weight: bolder;
					margin-bottom: 100rpx;
				}
			}
		}
	}
</style>