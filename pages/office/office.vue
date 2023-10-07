<template>
	<view class="container">
		<!-- 搜索框 -->
		<view class="search-box">
			<input v-model="searchQuery" placeholder="搜索科室名称" @input="handleSearch" />
		</view>

		<!-- 级联选择器 -->
		<view class="cascader">

			<u-form :model="model" ref="uForm">
				<u-form-item @click="open" label="需要的科室" prop="region" label-width="150">
					<!-- 监听input框的点击事件 -->
					<u-input type="select" v-model="model.region" placeholder="请选择科室"
						@click="open"></u-input>
				</u-form-item>
				<!-- 将u-picker的v-model绑定到pickerShow -->
				<u-picker @cancel="cancel" :show="show" ref="uPicker" :columns="columns" @confirm="confirm"
					@change="changeHandler"></u-picker>
			</u-form>
			<button type="default" @click="submit()">提交 </button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				model: {
					region: '',
				},
				searchQuery: "",
				show: true,
				columns: [
					['内科', '外科', '骨科', '妇产科', '儿科', '肿瘤科', '口腔科'],
					['普内科', '神经内科', '消化内科', '呼吸内科', '肾内科', '高压氧科', '内分泌科内分泌科'],
	
				],
				columnData: [
					['普内科', '神经内科', '消化内科', '呼吸内科', '肾内科', '高压氧科', '内分泌科'],
					['骨科', '眼科', '耳鼻喉科'],
					['骨科'],
					['妇产内科', '妇产外科',],
					['骨科', '眼科', '耳鼻喉科'],
					['骨科', '眼科', '耳鼻喉科'],
					['骨科', '眼科', '耳鼻喉科'],
				],
			};
		},
		methods: {
			changeHandler(e) {
				const {
					columnIndex,
					value,
					values, // values为当前变化列的数组内容
					index,
					// 微信小程序无法将picker实例传出来，只能通过ref操作
					picker = this.$refs.uPicker
				} = e
				// 当第一列值发生变化时，变化第二列(后一列)对应的选项
				if (columnIndex === 0) {
					// picker为选择器this实例，变化第二列对应的选项
					picker.setColumnValues(1, this.columnData[index])
				}
			},
			// 回调参数为包含columnIndex、value、values
			confirm(e) {
				console.log('confirm', e)
				this.show = false;
				this.model.region = e.value[0]+"-" +e.value[1];
			},

			submit() {
				console.log(this.model)
			},
			open() {
				this.show = true;
			},
			cancel(){
				this.show = false;
			}
		},
	};
</script>

<style>
	/* 样式可以根据自己的需求自定义 */
	.container {
		padding: 20px;
	}

	.search-box {
		margin-bottom: 20px;
	}

	.cascader {
		border: 1px solid #ccc;
		padding: 10px;
		border-radius: 5px;
	}

	.picker-text {
		font-size: 16px;
		color: #333;
		display: flex;
		align-items: center;
	}

	/* 添加蓝色竖线 */
	.picker-text::before {
		content: "";
		width: 4px;
		height: 100%;
		background-color: blue;
		margin-right: 10px;
	}
</style>