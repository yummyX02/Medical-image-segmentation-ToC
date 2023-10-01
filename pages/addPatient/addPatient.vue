<template>
	<view class="container">
		<h2>添加就诊人</h2>
		<u--input class="ipt" placeholder="真实姓名" v-model="value1" border="bottom" clearable></u--input>
		<view class="info">
			<text class="fic">证件类型</text>
			<u-radio-group class="fix" v-model="radiovalue1" placement="row" @change="groupChange">
				<u-radio :customStyle="{margin: '8px' }" v-for="(item, index) in radiolist1" :key="index"
					:label="item.name" :name="item.name" @change="radioChange">
				</u-radio>
			</u-radio-group>
			<u--input class="ipt" placeholder="证明号码" v-model="value2" border="bottom" clearable></u--input>
			<u--input class="ipt" placeholder="手机号码" v-model="value3" border="bottom" clearable></u--input>
			<u--input class="ipt" placeholder="验证码" v-model="value4" border="bottom" clearable></u--input>
		</view>
		<view class="footer">
			
			<button>确认</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				value1: "",
				value2: "",
				value3: "",
				value4: "",
				radiovalue1: "",
				radiolist1: [{
					name: "身份证"
				}, {
					name: "护照"
				}, {
					name: "军官证"
				}, {
					name: "港澳通行证"
				}, ]
			};
		},
		methods: {
			groupChange(n) {
				console.log('groupChange', n);
			},
			radioChange(n) {
				console.log('radioChange', n);
			}
		}
	}
</script>

<style lang="less">
	.container {
		padding: 20px;
		margin: 0 20px 0 20px;
		display: flex;
		flex-direction: column;

		.ipt {
			margin-top: 30px;
		}

		.fic {
			margin-top: 30px;
		}

		.fix {
			margin-top: 10px;
		}

		.info {
			display: flex;
			flex-direction: column;
		}

		.footer {
			margin-top: 100px;
			display: flex;
			justify-content: center;
			align-items: center;
			color: #fff;
			width: 200px;
			border-radius: 20px;

			button {
				background-color: #0379ff;
				width: 70%;
				color: #fff;
				border-radius: 25px;
			}

		}
	}
</style>