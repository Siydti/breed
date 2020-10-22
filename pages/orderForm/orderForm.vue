<template>
	<view class="orderForm">
		<view class="orderForm_list" v-for="(item,index) in orderForm_list" :key="index">
			<view class="orderForm_listTitle" >
				<image src="/static/img/ClaimMsg_log.png" style="width: 32rpx;height: 32rpx;margin-right: 20rpx;margin-left: 10rpx; border-radius: 12rpx;"></image>
				<text>{{item.title}}</text>
			</view>
			
			<view class="orderForm_listMain">
				<view class="orderForm_listMain_left">
					<image :src="item.imgurl" style="width: 100%;height: 100%;"></image>
				</view>
				
				<view class="orderForm_listMain_mid">
					<view>编号：<text>{{item.num}}</text></view>
					<view>性别：<text>{{item.sex}}</text></view>
					<view>体重：<text>{{item.weight}}</text></view>
					<view>认领时间：<text>{{item.time}}</text></view>
				</view>
				
				<view class="orderForm_listMain_right">
					x <text>{{item.checkedNum}}</text>
				</view>
			</view>
			
			<view class="orderForm_listFoot">
				<view class="orderForm_listFoot_left">
					<text>出售价格</text><image src="/static/img/modification.png" style="width: 28rpx;height: 28rpx;margin-left: 4rpx;"></image>
				</view>
				
				<view class="orderForm_listFoot_right">
					￥<text>{{item.price}}</text>
				</view>
			</view>
		</view>
	
		<view class="orderForm_btn" @click="go_tradingParticulars">
			提交
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				orderForm_list:[
					{ title: '波尔山羊' , imgurl: '/static/img/yang01.png' , num: '23023146' , sex: '公' , weight: '90kg' , time: '2020-06-06' , checkedNum : '1' , price : '1000.00' },
					{ title: '边区莱斯特羊' , imgurl: '/static/img/yang02.png' , num: '23023146' , sex: '公' , weight: '90kg' , time: '2020-06-06' , checkedNum : '1' , price : '1000.00' }
				]
			}
		},
		methods: {
			go_tradingParticulars() {
				uni.navigateTo({
					url:'/pages/list/list'
				})
			}
		}
	}
</script>

<style>
@import url("./orderForm.css");
</style>
