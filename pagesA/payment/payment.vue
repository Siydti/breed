<template>
	<view class="peyment">
		<view class="peyment_details">
			<view class="peyment_details_title">
				<view class="peyment_details_title_left"></view>
				<view class="peyment_details_titlemsg">
					详情
				</view>
			</view>

			<view class="peyment_details_listBox">
				<view class="peyment_details_list" v-for="(item,index) in detailsList" :key="index">
					<text style="color: #777777;font-size: 24rpx;">{{item.left}}</text>
					<text style="color: #333;font-size: 24rpx;">{{item.right}}</text>
				</view>
			</view>

			<image src="/static/img/connect.png" class="connect_img"></image>
		</view>

		<view class="peyment_msg">
			<view class="peyment_msg_title">
				<view class="peyment_msg_title_left"></view>
				<view class="peyment_msg_titleMsg">
					买家信息
				</view>
			</view>
			
			<view class="peyment_msg_listBox">
				
				<view class="peyment_msg_list" v-for="(item,index) in msgList" :key="index">
					<text style="color: #777777;font-size: 24rpx;">{{item.left}}</text>
					<text style="color: #333;font-size: 24rpx;">{{item.right}}</text>
				</view>
				
			</view>
		</view>

		<view class="allprice">
			<view class="allprice_left">
				总价
			</view>
			<view class="allprice_right">
				￥<text>510</text>
			</view>
		</view>

		<view class="pey_btn" @click="go_peysucceed">
			立即支付
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				detailsList: [{
						left: "产品编号",
						right: "No.2563265"
					},
					{
						left: "产品品种",
						right: "杜泊羊"
					},
					{
						left: "性别",
						right: "公"
					},
					{
						left: "出生日期",
						right: "2020.06.06"
					},
					{
						left: "认购数量",
						right: "2"
					}
				],
				msgList:[{
						left: "姓名",
						right: "田小甜"
					},
					{
						left: "性别",
						right: "女"
					},
					{
						left: "联系方式",
						right: "15826623667"
					},
					{
						left: "身份证号",
						right: "215623023025616589"
					},
					{
						left: "认购数量",
						right: "2"
					}
				]
			}
		},
		methods: {
			go_peysucceed() {
				uni.navigateTo({
				    url: '/pagesA/peysucceed/peysucceed'
				})
				}
		}
	}
</script>

<style>
	@import url("./payment.css");
</style>
