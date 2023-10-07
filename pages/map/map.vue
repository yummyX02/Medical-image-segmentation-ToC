<template>
	<view class="container">
		<map :latitude="latitude" :longitude="longitude" :scale="scale" :markers="marker" class="mapview">
		</map>
		<button>{{province}}{{city}}</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				latitude: 39.9042,
				longitude: 116.4074,
				scale: 14, // 设置地图的缩放级别
				marker: [{
					id: 0,
					latitude: 39.056627,
					longitude: 117.14436,
					iconPath: "../../static/icon-weizhi.png",
					title: "当前位置",
					width: 10,
					height: 10
				}],
				city: "",
				province: "",
				mes: "",
				show: true
			}
		},
		methods: {

		},
		onLoad() {
			// 在 Vue 组件内部创建一个指向组件实例的变量
			const vm = this;
			uni.getLocation({
				type: 'gcj02',
				geocode: true,
				success: function(res) {
					console.log('当前位置的经度：' + res.longitude);
					console.log('当前位置的纬度：' + res.latitude);
					vm.longitude = res.longitude;
					vm.latitude = res.latitude;
					console.log(res.address);
					vm.province = res.address.province;
					if (res.address.province === res.address.city) {
						vm.city = res.address.district;
					};
					uni.showToast({
						title: '获取位置成功',
						icon: 'success', // 提示图标，可选值：'success', 'loading', 'none'
						duration: 2000, // 提示显示时间，单位毫秒
						mask: true, // 是否显示透明蒙层，防止触摸穿透
						success: () => {
							console.log('消息提示已显示');
							// 等待3秒后返回上一级页面
							setTimeout(() => {
								uni.navigateBack({
									delta: 1, // 返回的页面数，1表示返回上一级
									success: () => {
										console.log('已返回上一级页面');
									},
									fail: () => {
										console.log('返回上一级页面失败');
									}
								});
							}, 3000); // 3秒延迟
							uni.setStorage({
								key: 'location',
								data: res.address.city,
								success: function () {
									console.log('success');
								}
							});
						},
						fail: () => {
							console.log('消息提示显示失败');
						}
					});
				},
				fail: (err) => {
					console.log('获取位置失败', err);
				}
			});

		}
	};
</script>

<style lang="less">
	.container {
		width: 100vw;
		height: 100vh;
		display: flex;
		flex-direction: column;
		justify-content: center;

		button {
			margin-top: 20px;
			border: none;
			background-color: #69aafc;
		}

		.mapview {
			width: 100%;
			height: 500px;
		}
	}
</style>