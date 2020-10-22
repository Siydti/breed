<template>
	<view class="transactionRecord">

		<view class="transactionRecord_title">
			<view v-for="(item,index) in title" :key="index" :class="{ 'transactionRecord_title_active' : index == active }"
			 @click="switchover(index)">
				{{item.title}}
			</view>
		</view>

		<view class="transactionRecord_list" v-show="active != 4">
			<view class="payDetail_list" v-for="(item,index) in payDetail_list" :key="index">

				<view class="payDetail_list_left">
					<view class="payDetail_list_left_money">
						{{item.type == "充值" ? '+' : '-'}}{{item.money}}
					</view>
					<view class="payDetail_list_left_type">
						{{item.type}}
					</view>
				</view>

				<view class="payDetail_list_right">
					<view class="payDetail_list_right_ucceed">
						{{item.ucceed}}
					</view>
					<view class="payDetail_list_right_time">
						{{item.time}}
					</view>
				</view>

			</view>



		</view>
		
		
		<view class="qiun-columns" v-show="active == 4">

			<view class="qiun-charts">
				<canvas canvas-id="canvasLineA" id="canvasLineA" class="charts" @touchstart="touchLineA"></canvas>
			</view>
		</view>

	</view>
</template>

<script>
	import uCharts from '../../wxcomponents/u-charts/u-charts/u-charts.js';
	var _self;
	var canvaLineA = null;
	export default {
		data() {
			return {
				cWidth: '',
				cHeight: '',
				pixelRatio: 1,
				categories: ["2012", "2013", "2014", "2015", "2016", "2017"],
				series: [{
					name: "成交量A", data:[35, 8, 25, 37, 4, 20], color: "#1890ff"
				}, {
					name: "成交量B", data:[70, 40, 65, 100, 44, 68], color: "#2fc25b"
				}, {
					name: "成交量B", data:[100, 80, 95, 150, 112, 132], color: "#facc14"
				}],
				title: [{
						title: '全部'
					},
					{
						title: '认养卖入'
					},
					{
						title: '全部委托'
					},
					{
						title: '仅看成交'
					},
					{
						title: 'K线图'
					}
				],
				active: 4,
				payDetail_list: [{
						money: 1000,
						type: '提现',
						ucceed: '成功',
						time: '2020-01-06 02.13'
					},
					{
						money: 1000,
						type: '充值',
						ucceed: '成功',
						time: '2020-01-06 02.13'
					},
					{
						money: 1000,
						type: '认养交易',
						ucceed: '成功',
						time: '2020-01-06 02.13'
					},
					{
						money: 1000,
						type: '转让交易',
						ucceed: '成功',
						time: '2020-01-06 02.13'
					},
					{
						money: 500,
						type: '管理费',
						ucceed: '成功',
						time: '2020-01-06 02.13'
					}
				],
			}
		},
		onLoad() {
			_self = this;
			this.cWidth = uni.upx2px(750);
			this.cHeight = uni.upx2px(500);
			this.getServerData();
		},
		methods: {
			getServerData() {
				let LineA = {
					categories : this.categories,
					series : this.series
				}
				// uni.request({
				// 	url: 'https://www.ucharts.cn/data.json',
				// 	data: {},
				// 	success: function(res) {
				// 		console.log(res.data.data)
				// 		let LineA = {
				// 			categories: [],
				// 			series: []
				// 		};
				// 		//这里我后台返回的是数组，所以用等于，如果您后台返回的是单条数据，需要push进去
				// 		LineA.categories = res.data.data.LineA.categories;
				// 		LineA.series = res.data.data.LineA.series;
				// 	}
				// });
						_self.showLineA("canvasLineA", LineA);
			},
			showLineA(canvasId, chartData) {
				canvaLineA = new uCharts({
					$this: _self,
					canvasId: canvasId,
					type: 'line',
					fontSize: 11,
					legend: {
						show: true
					},
					dataLabel: false,
					dataPointShape: true,
					background: '#FFFFFF',
					pixelRatio: _self.pixelRatio,
					categories: chartData.categories,
					series: chartData.series,
					animation: true,
					xAxis: {
						type: 'grid',
						gridColor: '#CCCCCC',
						gridType: 'dash',
						dashLength: 8
					},
					yAxis: {
						gridType: 'dash',
						gridColor: '#CCCCCC',
						dashLength: 8,
						splitNumber: 5,
						min: 10,
						max: 180,
						format: (val) => {
							return val.toFixed(0) + '元'
						}
					},
					width: _self.cWidth * _self.pixelRatio,
					height: _self.cHeight * _self.pixelRatio,
					extra: {
						line: {
							type: 'straight'
						}
					}
				});

			},
			touchLineA(e) {
				canvaLineA.showToolTip(e, {
					format: function(item, category) {
						return category + ' ' + item.name + ':' + item.data
					}
				});
			},
			switchover(index) {
				this.active = index
			}
		}
	}
</script>

<style>
	@import url("./transactionRecord.css");

	/*样式的width和height一定要与定义的cWidth和cHeight相对应*/
	.qiun-columns{
		margin-top: 30rpx;
	}
	
	.qiun-charts {
		width: 750upx;
		height: 500upx;
		background-color: #f2f2f2;
	}

	.charts {
		width: 750upx;
		height: 500upx;
		background-color: #f2f2f2;
	}
</style>
