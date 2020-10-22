<template>
	<view class="calim">
		<view class="icon van-icon van-icon van-icon-upgrade van-icon-upgrade" style="font-size: 32rpx;"></view>
		<view class="top">
			<view class="search">
				<van-search :value="value" shape="round" placeholder="请输入您想要搜索的内容" />
			</view>
			<view class="screen">
				<text style="margin-right: 10rpx;">|</text><text style="margin-right: 10rpx;">筛选</text>
				<image style="width: 30rpx;height: 40rpx;vertical-align: middle;" src="/static/img/ICON/screen.png" mode=""></image>
			</view>
		</view>
		
		<view class="manyCalim">
			<view class="calimImg" @click="toDetail(item.id)" v-for="(item,index) in data" :key="index">
				<image style="width: 338rpx;height: 324rpx;" :src="imgHead+item.image" mode=""></image>
				<text class="introducText">{{item.introduction}}</text>
				<view class="priceCalim">
					<text style="font-size: 22rpx;color: #FF8031;">￥</text>
					<text class="calimPrice">{{item.event_price}}</text>
				</view>
				<text style="text-decoration: line-through;color: #808080; font-size: 20rpx;">￥{{item.price}}</text>
				<image class="cartImg" style="width: 36rpx; height: 36rpx; border-radius: 50%;" src="/static/img/mess/cart.png"
				 mode=""></image>
			</view>

		</view>
	</view>
</template>

<script>
	import { get , imgHead } from '../../utils/request.js'
	
	export default {
		data() {
			return {
				data:[],//接口数据
				imgHead:'',
			}
		},
		methods: {
			toDetail(id) {
				uni.navigateTo({
					url: "/pagesA/calimDetail/calimDetail?id=" + id
				})
			}
		},
		onShow() {
			let _this = this
			
			_this.imgHead = imgHead
			let pageNum = 1
			
			get( 'sheepList' , { page : pageNum } , (res) => {
				console.log( res.data )
				
				_this.data = res.data
			} , (res) => {} )
		}
	}
</script>

<style>
	@import url("./calim.css");

	page {
		background-color: #F2F2F2;
	}
</style>
