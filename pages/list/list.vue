<template>
	<view class="list">
		<view class="list_title">
			<view class="list_title_main">
				<view class="list_title_img">
					<image src="/static/img/list_title.png" mode=""></image>
				</view>
				<view class="list_title_content">
					挂单交易成功
				</view>
			</view>
		</view>

		<view class="list_main">

			<view class="list_main_top">
				<view class="list_main_top_title">
					订单信息
				</view>
			</view>

			<view class="list_main_msg">
				<view class="list_main_msg_left">
					<view>订单编号：</view>
					<view>创建时间：</view>
				</view>

				<view class="list_main_msg_right">
					<view>2154616416</view>
					<view>2020.06.06</view>
				</view>
			</view>

			<view class="list_main_list">
				<view class="list_main_list_title">
					<view class="list_main_list_title_img">
						<image src="/static/img/list_main_title.png" mode=""></image>
					</view>
					<view class="list_main_list_title_content">
						波尔山羊
					</view>
				</view>

				<view class="list_main_list_main">
					<view class="list_main_list_main_left">
						<image src="/static/img/123.png" mode=""></image>
					</view>
					<view class="list_main_list_main_mid">
						<view> 编号：5555555 </view>
						<view> 性别： 公 </view>
						<view> 体重： 52kg </view>
						<view> 认领时间： 2020-01-01 </view>
					</view>
					<view class="list_main_list_main_right">
						￥259
					</view>
				</view>
			</view>

			<view class="btn_box">
				<view class="btn_left">
					返回首页
				</view>
				<view class="btn_right">
					查看订单
				</view>
			</view>


		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style>
	@import url("./list.css");
</style>
