<template>
	<view style="padding-bottom: 110rpx;">
		<view class="shopItem" v-for="item in arr" :key=item>
			<van-swipe-cell :right-width=" 85 ">
				<view class="selectImg">
					<image @click="selected" style="width: 40rpx;height: 40rpx;" src="/static/img/cart/select.png" mode=""></image>
					<view class="cartInfo">
						<view class="cartImgs">
							<image style="width: 168rpx;height: 168rpx;" src="/static/img/cart/cartImg.png" mode=""></image>
						</view>
						<view class="cartMess">
							<text style="font-size: 30rpx;">波尔山羊</text>
							<text class="sex">性别:{{"公"}}</text>
							<text class="largeNum">体重:{{"50kg"}}</text>
							<view class="cartPrice">
								<text class="priceIcon">￥</text>
								<text class="priceItem">{{(531).toFixed(2)}}</text>
							</view>
						</view>
					</view>
				</view>
				<view class="add">
					<van-stepper :value=num input-width="54rpx" custom-class='plus' button-size="40rpx" />
				</view>
				<view slot="right" class="del">删 除</view>
			</van-swipe-cell>

		</view>
		<view class="cartFooter">
			<view class="cartLeft">
				<view>
					<image @click="allSelected" style="width: 40rpx;height: 40rpx;" src="/static/img/cart/select.png" mode=""></image>
					<text>全选</text>
				</view>
				<view class="cartPrice">
					<text class="priceIcon">￥</text>
					<text class="priceItem">{{(531).toFixed(2)}}</text>
				</view>
				
			</view>
			<view class="cartRight">
				<view class="real">
					确认下单
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				num: 1,
				arr: [1, 2, 3, 4, 5, 6]
			}
		},
		methods: {
			selected() {

			}
		}
	}
</script>

<style scoped>
	@import url("./cart.css");
</style>
