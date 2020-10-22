<template>
	<view class="personal">

		<view class="personal_main">
			<view class="portrait">
				<view class="name">
					头像
				</view>
				<view class="right_box">
					<view class="img_portrait">
						<image src="/static/img/picture.png" mode=""></image>
					</view>

					<view class="img_right">
						<van-icon name="arrow" />
					</view>
				</view>
			</view>

			<van-cell value="爱放羊的田小甜" title="昵称" size="large" title-style="margin-left:50rpx" is-link />
			<van-cell value="田小甜" title="姓名" size="large" title-style="margin-left:50rpx" is-link />
			<van-cell value="18725655726" title="手机号" size="large" title-style="margin-left:50rpx" is-link />
			<van-cell value="102636589741523602" title="身份证号码" size="large" title-style="margin-left:50rpx" is-link />
			<van-cell value="自由职业者" title="职业" size="large" title-style="margin-left:50rpx" is-link />
		</view>
	
		<view class="personal_hint">
			{{ hint }}
		</view>
	
		<view class="personal_btn">
			确认
		</view>
	</view>


	</view>
</template>

<script>
	export default {
		data() {
			return {
				hint:'(注:姓名和身份证号请认真填写，之后不可更改)'
			}
		},
		methods: {

		}
	}
</script>

<style>
	@import url("./personal.css");
</style>
