<template>
	<view class="container">
		<view class="topBackground" style="background-image: url('/static/img/mine/background.png');">
			<view class="headPortrait">
				<view class="userinfo">
					<image src="/static/img/mine/headPortrait.png" mode=""></image>
					<view class="userName">
						爱养羊的小甜甜
					</view>
					<view class="uId">
						ID:{{phone}}
					</view>
				</view>
			</view>
		</view>
		<view class="userMess">
			<van-cell icon="/static/img/mine/personal.png" title="个人信息" size="large" title-style="margin-left:50rpx" is-link
			 link-type="navigateTo" url="/pages/personal/personal" />
			<van-cell icon="/static/img/mine/record.png" title="交易记录" size="large" title-style="margin-left:50rpx" is-link
			 link-type="navigateTo" url="/pages/record/record" />
			<van-cell icon="/static/img/mine/ClaimMsg.png" title="认领信息" size="large" title-style="margin-left:50rpx" is-link link-type="navigateTo" url="/pages/ClaimMsg/ClaimMsg"/>
			<van-cell icon="/static/img/mine/list.png" title="挂单交易" size="large" title-style="margin-left:50rpx" is-link link-type="navigateTo" url="/pages/list/list"/>
		</view>
		<view class="member">
			<view class="recommend">
				<image src="/static/img/mine/line.png" style="width: 283rpx;height: 4rpx;" mode=""></image>
				<text style="color: #666666;">会员推荐</text>
				<image src="/static/img/mine/line.png" style="width: 283rpx;height: 4rpx;transform: rotate(180deg);" mode=""></image>
			</view>
			<view class="manyCalim">
				<view class="calimImg">
					<image style="width: 338rpx;height: 324rpx;" src="/static/img/calimImg.png" mode=""></image>
					<text class="introducText">{{introduce}}</text>
					<view class="priceCalim">
						<text style="font-size: 22rpx;color: #FF8031;">￥</text>
						<text class="calimPrice">259</text>
					</view>
					<text style="text-decoration: line-through;color: #808080; font-size: 20rpx;">￥259</text>
					<image class="cartImg" style="width: 36rpx; height: 36rpx; border-radius: 50%;" src="/static/img/mess/cart.png"
					 mode=""></image>
				</view>
				<view class="calimImg">
					<image style="width: 338rpx;height: 324rpx;" src="/static/img/calimImg.png" mode=""></image>
					<text class="introducText">{{introduce}}</text>
					<view class="priceCalim">
						<text style="font-size: 22rpx;color: #FF8031;">￥</text>
						<text class="calimPrice">259</text>
					</view>
					<text style="text-decoration: line-through;color: #808080; font-size: 20rpx;">￥259</text>
					<image class="cartImg" style="width: 36rpx; height: 36rpx; border-radius: 50%;" src="/static/img/mess/cart.png"
					 mode=""></image>
				</view>
			</view>
		</view>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				phone: "15837804453",
				introduce: "波尔山羊肉厚而不肥，肉质细、肌肉内脂肪少、色泽纯正、多汁鲜嫩"
			}
		},
		methods: {
			phoneName() {
				let tel = this.phone
				tel = "" + tel;
				let newTel = tel.substr(0, 3) + "****" + tel.substr(7);
				this.phone = newTel
			}
		},
		onLoad() {
			this.phoneName()
		}
	}
</script>

<style>
	@import url("./mine.css");

	page {
		background-color: #F2F2F2;
	}
</style>
