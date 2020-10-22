<template>
	<view class="property">
		<view class="property_heard">
			<image src="/static/img/property_bac.png" style="width: 120%;height: 518rpx;position: relative;left: -10%;"></image>
			<view class="property_heardMain">

				<view class="property_heardMain_title" :style="{'width':'100%','height':topBarHei,'marginTop':topBarMarT,'textAlign':'center'}">
					<van-icon name="arrow-left" class="property_heardMain_titleLeft" />
					<view class="property_heardMain_titleMain">总资产</view>
					<view class="property_heardMain_titleRight"></view>
				</view>

				<view class="property_heardMain_price">
					￥ <text>1000.00</text>
				</view>

				<view class="property_heardMain_foot">
					<view class="property_heardMain_footLeft">
						<view>4</view>
						<view>持养数量</view>
					</view>
					<view class="property_heardMain_footRight">
						<view>+500</view>
						<view>持养盈亏</view>
					</view>
				</view>

			</view>

			<view class="asset_revamp_box" @click="go_transactionRecord">
				<image src="/static/img/ICON/asset_revamp.png" style="width: 100%;height: 100%;"></image>
			</view>
		</view>

		<view class="property_main">
			<image src="/static/img/goatsListTitle_bac.png" class="goatsListTitle_bac"></image>
			<image src="/static/img/goatsList_bac.png" class="goatsList_bac"></image>

			<view class="property_mainTitle">
				<view class="property_mainTitle_smallCircle" style="margin-right: 30rpx;"></view>
				<view class="property_mainTitle_bigCircle"></view>
				<view class="property_mainTitle_content">
					羊群列表
				</view>
				<view class="property_mainTitle_bigCircle" style="margin-right: 30rpx;"></view>
				<view class="property_mainTitle_smallCircle"></view>
			</view>

			<view class="property_mainList">
				<view class="property_mainList_title">
					<view>
						是否挂单
					</view>
					<view>
						编号
					</view>
					<view>
						羊名
					</view>
					<view>
						最新成本
					</view>
					<view>
						当前价格
					</view>
					<view>
						盈亏
					</view>
				</view>


				<view class="property_mainList_box">
					<view class="property_mainList_list" v-for="(item,index) in mainList" :key='index'>
						<view>
							<image :src="item.url" style="width: 28rpx;height: 28rpx;"></image>
						</view>
						<view>{{item.num}}</view>
						<view style="margin-right: 32rpx;">{{item.name}}</view>
						<view style="margin-right: 32rpx;">{{item.cost}}</view>
						<view style="margin-right: 24rpx;">{{item.nowprice}}</view>
						<view style="margin-right: 16rpx;">{{item.type}}</view>
					</view>
				</view>
			</view>
		</view>
		
		<view class="property_foot">
			<view class="property_price">
				￥<text>2000</text>
			</view>
			<view class="property_affirm" @click="go_orderForm ">
				确认挂单
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				topBarHei: '30rpx',
				topBarMarT: '30rpx',
				mainList: [{
						url: '/static/img/no.png',
						num: 'No.1563266',
						name: '波尔山羊',
						cost: '1000',
						nowprice: '500',
						type: '+500'
					},
					{
						url: '/static/img/yes.png',
						num: 'No.1563266',
						name: '波尔山羊',
						cost: '1000',
						nowprice: '500',
						type: '+500'
					},
					{
						url: '/static/img/no.png',
						num: 'No.1563266',
						name: '波尔山羊',
						cost: '1000',
						nowprice: '500',
						type: '+500'
					},
					{
						url: '/static/img/yes.png',
						num: 'No.1563266',
						name: '波尔山羊',
						cost: '1000',
						nowprice: '500',
						type: '+500'
					},
					{
						url: '/static/img/no.png',
						num: 'No.1563266',
						name: '波尔山羊',
						cost: '1000',
						nowprice: '500',
						type: '+500'
					}
				]
			}
		},
		methods: {
			getMobileInfo() { //获取胶囊按钮信息
				const menuButtonInfo = uni.getMenuButtonBoundingClientRect();
				console.log(menuButtonInfo)
				this.topBarHei = menuButtonInfo.height + 'px'
				this.topBarMarT = (menuButtonInfo.top + 1) + 'px'
			},
			go_orderForm() {
				uni.navigateTo({
					url:'/pages/orderForm/orderForm'
				})
			},
			go_transactionRecord() {
				uni.navigateTo({
					url:'/pages/transactionRecord/transactionRecord'
				})
			}
		},
		onLoad: function() {
			this.getMobileInfo();
		},
	}
</script>

<style>
	@import url("./property.css");
</style>
