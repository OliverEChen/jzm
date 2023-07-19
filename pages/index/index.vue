<template>
	<view class="page">
		<view class="banner">
			<image src="https://qiniu-web-assets.dcloud.net.cn/unidoc/zh/shuijiao.jpg" mode="widthFix"></image>
		</view>
		<view style="padding: 0 20rpx; transform: translateY(-100rpx);">
			<view class="form">
				<input type="text" placeholder="请输入车牌号" v-model="carNo">
				<button @tap="handleQuery">点击查询</button>
			</view>
			<view style="text-align: center;margin-bottom: 20rpx;">--查询结果--</view>
			<template v-for="item in queryData">
				<view class="card">
					<view>车牌号码：{{item.carNo}}</view>
					<view style="border: 1px solid #ccc;margin: 10rpx;"></view>
					<view>已取得网约车运输证</view>
					<view style="font-size: 24rpx;">(许可地：北京)</view>
				</view>
			</template>

		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				carNo: '',
				queryData: [],
				dataSource: [{
						no: '租341226800016',
						carNo: '皖KUM953蓝',
						carType: '小型轿车',
						ton: 5,
						range: '网络预约出租汽车客运',
						model: '东风雪铁龙DC7162LYEM',
						firstDate: '11/12/21',
						status: '营运'
					},
					{
						no: '租341226800016',
						carNo: '贵FUM953蓝',
						carType: '小型轿车',
						ton: 5,
						range: '网络预约出租汽车客运',
						model: '东风雪铁龙DC7162LYEM',
						firstDate: '11/12/21',
						status: '营运'
					},
					{
						no: '租341226800016',
						carNo: '沪CUM953蓝',
						carType: '小型轿车',
						ton: 5,
						range: '网络预约出租汽车客运',
						model: '东风雪铁龙DC7162LYEM',
						firstDate: '11/12/21',
						status: '营运'
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			handleQuery() {
				console.log(this.carNo)
				if(this.carNo){
					this.queryData = this.dataSource.filter((item) => item.carNo.includes(this.carNo))
				}else {
					this.queryData = []
				}

			}
		}
	}
</script>

<style lang="scss">
	.page {
		.card {
			background-color: #bed5f4;
			padding: 20rpx;
			margin-bottom: 10rpx;

			&>view {
				margin: 6rpx 0;
			}
		}

		.form {
			padding: 20rpx;
			background-color: #fff;

			input {
				height: 80rpx;
				border: 2rpx solid #244FD6;
				border-radius: 20rpx;
			}

			button {
				margin-top: 30rpx;
				height: 80rpx;
				background: #244FD6;
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