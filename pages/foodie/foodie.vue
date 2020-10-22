<template>
	<view class="foodie">
		<view class="foodie_top">
			<view class="foodie_top_left">
				<view class="foodie_top_left_top">
					田小甜
				</view>
				<view class="foodie_top_left_bottom">
					默认
				</view>
			</view>
			<view class="foodie_top_mid">
				<view class="foodie_top_mid_top">
					15826623663
				</view>
				<view class="foodie_top_mid_bottom">
					地址：东海省东海市龙宫路28号
				</view>
			</view>
			<view class="foodie_top_right" >
				<view class="foodie_top_right_top" @click="go_setSite">
					<image src="/static/img/amend.png" style="width: 24rpx;height: 24rpx;margin-right: 4rpx;"></image>
					<text>修改</text>
				</view>
				<view class="foodie_top_right_top">
					
				</view>
			</view>
		</view>
	
		<view class="foodie_main">
			
			<view class="foodie_main_title">
				<view class="foodie_main_title_left"></view>
				<view class="foodie_main_title_content">
					工单填写
				</view>
			</view>
			
			<view class="foodie_mainList">
				<view class="foodie_mainList_left">
					屠宰日期
				</view>
				<view class="foodie_mainList_right">
					2020.07.07
					<text> > </text>
				</view>
			</view>
			
			<view class="foodie_mainList">
				<view class="foodie_mainList_left">
					包装方式
				</view>
				<view class="foodie_mainList_right">
					精品包装
					<text> > </text>
				</view>
			</view>
			
			<view class="foodie_mainList">
				<view class="foodie_mainList_left">
					冷藏方式
				</view>
				<view class="foodie_mainList_right">
					冷冻
					<text> > </text>
				</view>
			</view>
			
			<view class="foodie_mainList">
				<view class="foodie_mainList_left">
					宰割数量
				</view>
				<view class="foodie_mainList_right">
					2
					<text> > </text>
				</view>
			</view>
			
		</view>
	
		<view class="foodie_btn">
			确认
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {

		},
		methods: {
			go_setSite() {
				console.log( 1 )
				uni.navigateTo({
					url:'/pages/setSite/setSite'
				})
			}
		}
	}
</script>

<style>
@import url("./foodie.css");
</style>
