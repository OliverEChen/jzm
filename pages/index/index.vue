<template>
	<view class="page">
		<view class="banner"><image src="https://qiniu-web-assets.dcloud.net.cn/unidoc/zh/shuijiao.jpg" mode="widthFix"></image></view>
		<view style="padding: 0 20rpx; transform: translateY(-100rpx);">
			<view class="form">
				<input type="text" placeholder="请输入车牌号" v-model="carNo" />
				<button @tap="handleQuery">点击查询</button>
			</view>
			<view style="text-align: center;margin-bottom: 20rpx;">--查询结果--</view>
			<template v-for="item in queryData">
				<view class="card">
					<view class="flex" style="width: 80vw;overflow: auto;">
						<view class="carNo flex common">
							<view class="label">车牌号</view>
							<view>{{ item.carNo }}</view>
						</view>
						<view class="seat flex common">
							<view class="label">吨(座)位</view>
							<view>{{ item.ton }}</view>
						</view>
						<!-- <view class="brand flex common">
							<view class="label">品牌</view>
							<view>品牌</view>
						</view> -->
					</view>
					<view class="flex">
						<view class="title">经营范围:</view>
						<view class="text">{{ item.range }}</view>
					</view>
					<view class="flex">
						<view class="title">首次发证日期:</view>
						<view class="text">{{ item.firstDate }}</view>
					</view>
					<view class="flex">
						<view class="title">厂牌型号:</view>
						<view class="text">{{ item.model }}</view>
					</view>
					<view class="flex">
						<view class="title">车辆类型:</view>
						<view class="text">{{ item.carType }}</view>
					</view>
					<view class="flex">
						<view class="title">车辆状态:</view>
						<view class="text">{{ item.status }}</view>
					</view>
					<view class="flex">
						<view class="title">所属公司:</view>
						<view class="text">{{ item.company }}</view>
					</view>
				</view>
			</template>
		</view>
	</view>
</template>

<script>
import { data } from './data.js';
export default {
	data() {
		return {
			title: 'Hello',
			carNo: '皖KDE9529绿',
			queryData: [],
			dataSource: []
		};
	},
	onLoad() {},
	methods: {
		handleQuery() {
			console.log(this.carNo);
			if (this.carNo) {
				this.queryData = data.filter(item => item.carNo.includes(this.carNo));
			} else {
				this.queryData = [];
			}
		}
	}
};
</script>

<style lang="scss">
.text {
	color: #4d77ab;
}
.flex {
	display: flex;
}
.common {
	& > view {
		padding: 5rpx 10rpx;
	}
}
.carNo {
	.label {
		color: #fff;
		background: #c69905;
	}
	color: #c69905;
	border: 1px solid #c69905;
}
.seat {
	.label {
		color: #fff;
		background: #c65f06;
	}
	color: #c65f06;
	border: 1px solid #c65f06;
	margin: 0 10rpx;
}
.brand {
	.label {
		color: #fff;
		background: #3d71b8;
	}
	color: #3d71b8;
	border: 1px solid #3d71b8;
}
.label {
}
.page {
	.card {
		border: 1px solid #ccc;
		padding: 20rpx;
		margin-bottom: 10rpx;

		& > view {
			margin: 6rpx 0;
		}
	}

	.form {
		padding: 20rpx;
		background-color: #fff;

		input {
			padding: 0 20rpx;
			height: 80rpx;
			border: 2rpx solid #244fd6;
			border-radius: 20rpx;
		}

		button {
			margin-top: 30rpx;
			height: 80rpx;
			background: #244fd6;
			border-radius: 40rpx;
			color: #fff;
		}
	}

	.banner {
		image {
			width: 100%;
		}
	}
}
</style>
