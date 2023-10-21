<template>
<view class="container">
	<view class="mid">
		<view v-for="chat in chatList[id]" :key="chat.id" class="mes">
			<view :class="{ doctor: chat.isDoctor, patient: !chat.isDoctor }">
				<img v-if="chat.isDoctor" src="../../static/doctor.png" alt="" srcset="" class="avatar" />
				<view class="mes">
					<text>{{ chat.info }}</text>
				</view>
				<img v-if="!chat.isDoctor" src="../../static/patient.jpg" alt="" srcset="" class="avatar" />
			</view>
		</view>
	</view>
	<view class="bottom">
		<input type="text" class="chat-input" placeholder="输入消息">
		<button  class="send-button">发送</button>
	</view>
</view>
</template>

<script>
	export default {
		data() {
			const id = 0;
			const MesList = [{
					name: "王白白",
					sex: "男",
					age: "20",
					info: "天天头疼,掉头发，睡不好觉，持续很久了，是什么怎么回事呢? ?",
					status: "已回复",
					headUrl: "../assets/patient.jpg",
				},
				{
					name: "李德",
					sex: "男",
					age: "60",
					info: "发烧,而且还伴有流涕的症状",
					status: "已回复",
					headUrl: "../assets/patient.jpg",
				},
				{
					name: "刘东",
					sex: "男",
					age: "20",
					info: "失眠，无法入睡 ",
					status: "未读",
					headUrl: "../assets/patient.jpg",
				},
			];
			const chatList = [
				[{
						id: 0,
						info: "这种症状是什么时候开始的呢? 想服用一些药物吗?",
						isDoctor: true,
					},
					{
						id: 1,
						info: "大概已经有两周左右的时间了，期间自己吃够一些药，但是作用不是很大...",
						isDoctor: false,
					},
					{
						id: 2,
						info: "你好，你的掉发和头痛考虑还是失眠不好失眠导致的。失眠多跟长期过度用脑，起居无规律，脏腑失调，情志郁结等因素有关可在医生的指导下使用可以口服;谷维素片+维生素B1片+安神补脑液养血安神丸或者枣仁安神颗粒进行治疗，入睡困难建议口服地西洋片,建议要平时要多吃坚果类食物，例如核桃，葵花籽等，合理安排自己的作息时间，避免劳累，保持心情舒畅也是很重要的，另外养成良好的休息习惯,避免劳累,缓解自己的压力,保持愉快的心情.祝您早日康复!",
						isDoctor: true,
					},
				],
				[{
						id: 0,
						info: "发烧流鼻涕首先应该补充大量的水分，摄入适量的瓜果蔬菜，同时要测量一下体温，如果体温过高，可以在医生的指导下口服退烧药。发烧流鼻涕应该是感冒引起的，一般不需要太过担心，保证良好的睡眠质量有利于身体的康复。",
						isDoctor: true,
					},
					{
						id: 1,
						info: "我这个可能是什么原因造成的呢？",
						isDoctor: false,
					},
					{
						id: 2,
						info: "发热一直流鼻涕可能是因为病毒性感冒、细菌性感冒、支气管炎等原因所引起，要对症处理，可以用解热镇痛药物、抗过敏药物进行局部的处理，比如选用氨加黄敏胶囊或者氯苯那敏等药物，都能起到不错的效果。其次，对症处理发烧，如果体温过高，超过38.5摄氏度以上，可以选择适当的退烧药物进行治疗，可以选用非甾体类抗炎药，比如牛黄安宫丸、布洛芬、芬必得等。",
						isDoctor: true,
					},
				],
			];
			return {
				id,
				MesList,
				chatList
			}
		},
		methods: {

		},
		onLoad() {
			this.id = uni.getStorageSync("chatIndex");
			console.log(this.id);
		}
	}
</script>

<style>
	.bottom {
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 10px;
		background-color: #f5f5f5;
		border-top: 1px solid #ccc;
		margin-top: 80px;
	}

	.chat-input {
		flex: 1;
		padding: 10px;
		border: 1px solid #ccc;
		border-radius: 5px;
		margin-right: 10px;
	}

	.send-button {
		background-color: #2b86f1;
		color: #fff;
		border: none;
		border-radius: 5px;
		padding: 10px 20px;
		cursor: pointer;
	}

	.avatar {
		width: 50px;
		height: 50px;
		border-radius: 50px;
	}

	.mid {
		padding: 10px;
		width: 100%;

		.doctor {
			display: flex;
			justify-content: flex-start;
			margin: 10px;

			.mes {
				width: 300px;
				height: auto;
				background-color: #fff;
				border-radius: 10px;
				margin-right: 10px;
				//灰色阴影
				box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
				text-align: left;
				padding: 10px;
			}
		}

		.patient {
			display: flex;
			margin: 10px;
			justify-content: flex-end;
			.mes {
				width: 300px;
				height: auto;
				background-color: #fff;
				border-radius: 10px;
				margin-right: 10px;
				//灰色阴影
				box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
				text-align: left;
				padding: 10px;
			}
		}
	}
</style>