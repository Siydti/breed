<template>
	<view class="message"> 
		<view class="icon van-icon van-icon van-icon-upgrade van-icon-upgrade" style="font-size: 32rpx;"></view>
		<view class="top">
			<view class="search">
				<van-search
				  :value="value"
				  shape="round"
				  placeholder="请输入您想要搜索的内容"
				/>
			</view>
			<view class="screen" @click="screenClick">
				<text style="margin-right: 10rpx;">|</text><text style="margin-right: 10rpx;">筛选</text><image style="width: 30rpx;height: 40rpx;vertical-align: middle;" src="/static/img/ICON/screen.png" mode=""></image>
				<view class="smallTriangle" v-if="screenShow">
					
				</view>
			</view>
		</view>
		<view class="screenBar" v-if="screenShow">
			<view v-for="(item,index) in screenBarItem" :key=index @click="select(index)" :class="index==ind?'selectColor':''">{{item}}<image class="triangle" src="/static/img/mess/sanjiao.png" mode="widthFix"></image><text v-if="index!=3" style="margin-left: 35rpx; color: #FFFFFF;">|</text></view>
		</view>
		<view class="manyCalim">
			<view class="calimImg" @click="go_howCalim">
				<image style="width: 338rpx;height: 324rpx;" src="/static/img/calimImg.png" mode=""></image>
				<text class="introducText">{{introduce}}</text>
				<view class="priceCalim">
					<text style="font-size: 22rpx;color: #FF8031;">￥</text>
					<text  class="calimPrice">259</text>
				</view>
				<text style="text-decoration: line-through;color: #808080; font-size: 20rpx;">￥259</text>
				<image class="cartImg" style="width: 36rpx; height: 36rpx; border-radius: 50%;" src="/static/img/mess/cart.png" mode=""></image>
			</view>

		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				screenBarItem:["价格","性别","热销榜","体重"],
				ind:null,
				screenShow:false,
				introduce:"波尔山羊肉厚而不肥，肉质细、肌肉内脂肪少、色泽纯正、多汁鲜嫩"
			}
		},
		methods: {
			//筛选下每一项
			select(index){
				this.ind = index
			},
			//点击筛选
			screenClick(){
				this.screenShow = !this.screenShow
			},
			go_howCalim() {
				uni.navigateTo({
					url: '/pagesA/howCalim/howCalim'
				})
			}
		}
	}
</script>

<style>
	@import url("./message.css");
page{
	background-color: #F2F2F2;
}
</style>
