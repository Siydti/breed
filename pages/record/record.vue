<template>
	<view class="record">

		<view class="record_top_box" style="background-image:url('/static/img/record_bac.png');">
			<view class="record_top">
				<view class="record_top_balance">
					98.00
				</view>
				<view class="record_top_hint">
					账户余额（元）
				</view>
			</view>
		</view>

		<van-cell icon="paid" is-link class="cell_box" size="large" link-type="navigateTo"
  url="/pagesA/deposit/deposit">
			<view slot="title">
				<view class="van-cell-text">提现</view>
			</view>
		</van-cell>

		<view class="record_list_title">
			<view class="record_list_title_left">
				交易明细
			</view>

			<view class="record_list_title_right" @click="go_payDetail">
				<view class="record_list_title_right_content">
					查看更多
				</view>
				<view class="record_list_title_right_icon">
					<van-icon name="arrow" />
				</view>
			</view>
		</view>

		<view class="record_list" v-for="(item,index) in record_list" :key="index">

			<view class="record_list_left">
				<view class="record_list_left_money">
					{{item.type == "充值" ? '+' : '-'}}{{item.money}}
				</view>
				<view class="record_list_left_type">
					{{item.type}}
				</view>
			</view>

			<view class="record_list_right">
				<view class="srecord_list_right_ucceed">
					{{item.ucceed}}
				</view>
				<view class="record_list_right_time">
					{{item.time}}
				</view>
			</view>

		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				record_list: [{
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
				]
			}
		},
		methods: {
			go_payDetail() {
				uni.navigateTo({
					url: '/pagesA/payDetail/payDetail'
				})
			}
		}
	}
</script>

<style>
	@import url("./record.css");
</style>
