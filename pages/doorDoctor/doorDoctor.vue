<template>
	<view class="container">
		<view class="card-top">
			<view class="doctor">
				<view class="info-top">
					<view class="left">
						<img src="../../static/doctor1.jpg" alt="" srcset="">
					</view>
					<view class="right">
						<view class="title">
							<h2>{{name}}</h2>
							<h3>{{degree}}</h3>
						</view>
						<view class="identify">
							{{identify}}
						</view>
					</view>
				</view>
				<view class="mid">
					<view class="list">
						<text>就诊医院科室</text>
						<text>{{office}}</text>
					</view>
					<view class="list">
						<text>门诊时间</text>
						<text>{{time}}</text>
					</view>
					<view class="list">
						<text>门诊类型</text>
						<text>{{type}}</text>
					</view>
					<view class="list">
						<text>医师服务费</text>
						<text>{{money}}</text>
					</view>
				</view>
				<view class="bottom">
					<view class="title">
						<u-icon name="info-circle-fill" color="#ffa905"></u-icon>
						<text>门诊预约挂号须知</text>
						<text>(预约即代表同意以下规则)</text>
					</view>
					<text>1.医事服务费由医院设定本平台不收取任何额外费用</text>
					<text>2.停诊将短信通知，请保持手机畅通</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				identify:"北京协和医院博士生导师",
				name:"王医生",
				degree:"主任医师",
				office:"北京协和医院-神经内科",
				time:"2020年05月05日周四下午",
				type:"专家门诊",
				money:"318元",
			};
		}
	}
</script>

<style lang="less">
.container{
	
	
}
</style>
