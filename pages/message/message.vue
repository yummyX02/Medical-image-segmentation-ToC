<template>
	<!-- //页面12 -->
	<view class="container">
		<div class="card" v-for="(item,index) in patients" :key="index">
			<div class="left">
				<img src="../../static/patient.jpg" alt="" srcset="" style="width: 50px;height: 50px;">
			</div>
			<div class="right">
				<view class="top">
					<h3 class="title">{{item.name}}</h3>
					<div class="date">{{item.date}}</div>
				</view>
				<span class="text">{{item.des}}</span>
			</div>
		</div>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				patients:[
					{
						name:"王白白",
						sex:"男",
						date:"2023-10-11",
						age:20,
						des:"你好，你的掉发和头痛考虑还是失眠不好失眠导致的。失眠多跟长期过度用脑，起居无规律，脏腑失调,情志郁结等因素有关可在医生的指导下使用可以口服;谷维素片+维生素B1片+安神补脑液养血安神丸或者枣仁安神颗粒进行治疗，入睡困难建议口服地西洋片,建议要平时要多吃坚果类食物，例如核桃，葵花籽等，合理安排自己的作息时间，避免劳累，保持心情舒畅也是很重要的，另外养成良好的休息习惯，避兔劳累,缓解自己的压力,保持愉快的心情.祝您早日康复!"
					},{
						name:"李德",
						sex:"男",
						date:"2023-10-10",
						age:60,
						des:"发热一直流鼻涕可能是因为病毒性感冒、细菌性感冒、支气管炎等原因所引起，要对症处理，可以用解热镇痛药物、抗过敏药物进行局部的处理，比如选用氨加黄敏胶囊或者氯苯那敏等药物，都能起到不错的效果。其次，对症处理发烧，如果体温过高，超过38.5摄氏度以上，可以选择适当的退烧药物进行治疗，可以选用非甾体类抗炎药，比如牛黄安宫丸、布洛芬、芬必得等。"
					},{
						name:"刘东",
						sex:"男",
						date:"2023-10-05",
						age:20,
						des:"尽量每天都在相同的时间上床睡觉和起床，包括周末。这有助于调整生物钟，使您的身体更容易入睡和醒来。避免在睡觉前喝含咖啡因的饮料，如咖啡和茶，以及酒精。这些物质可以影响睡眠质量。"
					},
					
				]
			};
		}
	}
</script>

<style lang="less">
	.container {
		display: flex;
		flex-direction: column;
		margin-top: 20px;
		align-items: center;
	}

	.card {
		display: flex;
		align-items: center;
		border: 1px solid #ccc;
		padding: 10px;
		box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2);
		/* 添加立体效果 */
		transition: box-shadow 0.3s ease;
		/* 添加过渡效果 */
		width: 80vw;
		border: none;
		border-radius: 10px;
		margin-top: 20px;
	}

	.card:hover {
		box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3);
		/* 鼠标悬停时增加更强的立体效果 */
	}

	.left {
		margin-right: 10px;
	}

	.icon {
		/* 添加图标样式，可以使用字体图标或图片 */
		font-size: 24px;
	}

	.right {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		margin-left: 20px;
	}

	.title {
		font-size: 18px;
		margin: 0;
	}

	.date {
		color: #666;
		font-size: 14px;
	}

	.text {
	    color: #666;
	    font-size: 12px;
	    margin-top: 10px;
	    white-space: nowrap; // 文本不换行
	    overflow: hidden; // 超出隐藏
	    text-overflow: ellipsis; // 超出部分使用省略号
	    max-width: calc(50vw - 20px); // 限制宽度，考虑到 .right 的 margin
	  }
	.top{
		display: flex;
		justify-content: space-between;
		width: 65vw;
	}
</style>