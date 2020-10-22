<template>
	<view class="growthDynamic">
		<image src="/static/img/growthDynamic_bac.png" style="width: 105%;height: 105%;position: relative;left: -30rpx;top: -5rpx;"></image>

		<view class="title_box">
			<image src="/static/img/title_bac.png" class="img_title"></image>
			<text class="title">成长动态报告</text>
		</view>


		<view class="main_box">
			<image src="/static/img/main_bac.png" class="img_main"></image>

			<view class="main_listBox">
				<view class="main_list" v-for="(item,index) in mainList" :key="index">
					<view class="main_list_left">
						{{item.title}}
					</view>
					<view class="main_list_mid">
						<view>
							<view>{{item.num}}</view>
						</view>
						{{item.unit}}
					</view>
					<view class="main_list_right">
						<image src="/static/img/up_btn.png" style="width: 43rpx;height: 34rpx;"></image>
						<view class="right_top">
							{{item.upnum}}
						</view>
					</view>
				</view>

				<view class="main_listEnd">
					<view class="main_list_left">
						生长周期
					</view>
					<view class="main_list_mid">
						<view>
							<view>8</view>
						</view>周
					</view>
					<view class="main_list_right">
						
					</view>
				</view>

			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				mainList: [{
						title: '体重',
						num: '50',
						unit: 'KG',
						upnum: '+10kg'
					},
					{
						title: '长度',
						num: '150',
						unit: 'CM',
						upnum: '+50cm'
					},
					{
						title: '高度',
						num: '100',
						unit: 'CM',
						upnum: '+50cm'
					}
				]
			}
		},
		methods: {

		}
	}
</script>

<style>
	@import url("./growthDynamic.css");
</style>
