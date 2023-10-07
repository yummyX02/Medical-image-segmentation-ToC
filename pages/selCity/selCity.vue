<template>
	<view class="container">
		<view class="search-container">
			<input class="search-box" type="text" placeholder="搜索城市名称" v-model="searchText" />
		</view>

		<view class="lists-container">
			<view class="hot-list">
				<view class="hot-cities">
					<view class="divider"></view>
					<text class="hot-city">热门城市</text>
				</view>
				<ul>
					<li v-for="city in hotCities" :key="city" @click="navigateToCity(city)">{{ city }}</li>
				</ul>
			</view>

			<view class="national-list">
				<view class="national-cities">
					<text class="location">定位城市</text>
					<ul>
						<li v-for="city in nationalCities" :key="city" @click="navigateToCity(city)">{{ city }}</li>
					</ul>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				searchText: '', // 用于存储搜索文本
				hotCities: ['北京', '上海', '广州', '西安', '天津'], // 热门城市示例
				nationalCities: [ // 全国城市示例
					'北京', '上海', '广州', '深圳', '天津', '重庆', '成都', '杭州', '南京', '武汉',
					'西安', '郑州', '长沙', '青岛', '沈阳', '大连', '苏州', '无锡', '济南', '厦门',
					'宁波', '福州', '合肥', '南昌', '长春', '哈尔滨', '南宁', '昆明', '贵阳', '石家庄',
					'太原', '西宁', '兰州', '银川', '呼和浩特', '乌鲁木齐', '拉萨', '海口', '澳门', '香港'
					// 在这里添加更多省市
				],
			};
		},
		methods: {
			navigateToCity(city) {
				uni.navigateTo({
					url:'/pages/hospitalList/hospitalList'
				})
				uni.setStorage({
					key:'city',
					data:city,
					success() {
						console.log("success",city);
					}
				})
			},
		},
	};
</script>

<style scoped>
	.container {
		font-family: Arial, sans-serif;
		padding: 20px;
	}

	.search-container {
		text-align: center;
		padding: 20px;
	}

	.search-box {
		width: 70%;
		height: 30px;
		padding: 10px;
		font-size: 16px;
		border: 1px solid #ccc;
		border-radius: 15px;
		background-color: #f7f8ff;
		margin: 0 auto;
	}

	.search-button {
		padding: 10px 20px;
		font-size: 16px;
		background-color: #007BFF;
		color: white;
		border: none;
		border-radius: 5px;
		cursor: pointer;
		transition: background-color 0.2s ease;
	}

	.search-button:hover {
		background-color: #0056b3;
	}

	.lists-container {
		display: flex;
		justify-content: space-between;
		margin-top: 20px;
	}

	.hot-list {
		width: 48%;
		/* 调整宽度以适应您的设计 */
	}

	.national-list {
		width: 48%;
		/* 调整宽度以适应您的设计 */
	}

	.hot-cities {
		display: flex;
		align-items: center;
	}

	.divider {
		width: 3px;
		height: 20px;
		background-color: blue;
		margin-right: 10px;
	}

	.hot-city {
		font-size: 18px;
		font-weight: bold;
	}

	.national-cities {
		margin-top: 20px;
	}

	.location {
		font-weight: bold;
	}

	ul {
		list-style-type: none;
		padding: 0;
	}

	li {
		margin: 5px 0;
	}
</style>