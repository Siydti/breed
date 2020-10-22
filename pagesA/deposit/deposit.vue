<template>
	<view class="deposit">
		<view class="deposit_main">
			<view style="margin-bottom: 54rpx;">
				账户余额 <text class="price">{{price}}</text>元
			</view>
			<view style="margin-bottom: 30rpx;">
				提现金额
			</view>
			<view class="input_box uni-form-item uni-column" >
				<text>￥</text>
				<input class="uni-input" type="number" :value=value />
			</view>
			
			<view>
				提现到微信钱包，<text class="all_btn" @click="all_btn">全部提现</text>
			</view>
			
			<view class="deposit_btn">
				提现
			</view>
			
			<view class="deposit_hint">
				1-5个工作日到账
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				price: '98.00',
				value: ''
			}
		},
		methods: {
			all_btn() {
				this.value = this.price
			}
		}
	}
</script>

<style>
	@import url("./deposit.css")
</style>
