<template>
	<view class="setSite">

		<view class="setSite_main">
			<view class="setSite_consignee">
				<view class="setSite_left">
					收货人
				</view>
				<view class="setSite_right">
					<input type="text" placeholder="请填写姓名" />
				</view>
			</view>

			<view class="setSite_phone">
				<view class="setSite_left">
					联系电话
				</view>
				<view class="setSite_right">
					<input type="text" placeholder="请填写联系电话" />
				</view>
			</view>

			<view class="setSite_site">
				<view class="setSite_left">
					所在地区
				</view>
				<view class="setSite_right">
					<text>请选择省、市、区</text>
					<van-icon name="arrow" style="margin-right: 32rpx;"/>
				</view>
			</view>

			<view class="setSite_text">
				<textarea placeholder="请填写详细地址(街道、楼牌号等)" />
				</view>
		</view>
		
		<view class="setDefault">
			<view class="setDefault_left">
				设为默认地址
			</view>
			<van-switch :checked="checked" @change="onChange" class="setDefault_right" size="40rpx" active-color="#FF6C00"  inactive-color="#F4F3F8"/>
		</view>
		
		<view class="btn_box">
			确认
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				checked:false,//设置是否开启默认地址
			}
		},
		methods: {
			onChange() {
			    this.checked = !this.checked
			  },
		}
	}
</script>

<style>
@import url("./setSite.css");
</style>
