<template>
	<view class="peysucceed">
		<view :style="{'width':'100%','height':topBarHei,'marginTop':topBarMarT,'textAlign':'center','borderBottom':'1rpx solid #dedede'}" class="peysucceed_topBar">支付成功</view>
		
		<view class="peysucceed_title">
			<image src="/static/img/list_title.png" style="width: 68rpx;height: 68rpx;margin-right: 24rpx;"></image>
			<text style="color: #333;font-size: 50rpx;">订单支付成功</text>
		</view>
		
		<view class="peysucceed_listBox">
			
			<view class="peysucceed_listTitle">
				订单信息
			</view>
			
			<view class="peysucceed_list" v-for="(item,index) in list" :key="index">
				<view class="peysucceed_list_left">
					{{item.left}}
				</view>
				
				<view class="peysucceed_list_right">
					{{item.right}}
				</view>
			</view>
			
		</view>
		
			<view class="peysucceed_btnBox">
				<view class="peysucceed_btnBox_left" @click="go_index">
					返回首页
				</view>
				
				<view class="peysucceed_btnBox_right" @click="go_ClaimMsg">
					查看订单
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
				list:[
					{ left : "订单号" , right : "5126959994023" },
					{ left : "支付方式" , right : "微信支付" },
					{ left : "订单金额" , right : "￥510.00" },
					{ left : "支付时间" , right : "2020.06.06 09:30" }
				]
			}
		},
		methods: {
			getMobileInfo() {//获取胶囊按钮信息
				const menuButtonInfo = uni.getMenuButtonBoundingClientRect();
				console.log( menuButtonInfo )
				this.topBarHei = menuButtonInfo.height + 'px'
				this.topBarMarT = (menuButtonInfo.top+1 )+ 'px'
			},
			go_index() {
				console.log( 11 )
				uni.navigateBack({
					 delta: 100
				})
			},
			go_ClaimMsg() {
				uni.navigateTo({
					url:'../../pages/ClaimMsg/ClaimMsg'
				})
			}
		},
		onLoad: function () {
		    this.getMobileInfo();
		  },
	}
</script>

<style>
@import url("./peysucceed.css");
</style>
