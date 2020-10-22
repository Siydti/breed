<template>
	<view class="calimDetail">
		<!-- 轮播 -->
		<view class="detailTop">
			<swiper style="height: 500rpx;" :autoplay="true" :interval="3000" :duration="1000" @change="swiperImg">
				<swiper-item v-for="(item,idnex) in imgArr" :key="index">
					<image style="width: 100%;height: 500rpx;" src="/static/img/detailImg.png"></image>
				</swiper-item>
			</swiper>
			<view class="back">
				<image style="width: 44rpx;height: 44rpx; margin-right: 11rpx;" src="/static/img/detailBack.png" @click="go_back"></image>
			</view>
			<view class="imgNum">
				<image style="width: 17rpx;height: 18rpx;" src="/static/img/imgIcon.png" mode=""></image>
				<text style="font-size: 20rpx;">{{num}}/</text>
				<text style="font-size: 20rpx;">{{imgArr.length}}</text>
			</view>
		</view>

		<view class="detail_main">


			<view class="detail_title">
				<text style="color: #000000;font-size: 28rpx;font-weight: bold;">杜泊羊</text>
				<text style="color: #666666;font-size: 20rpx;">No.2563265</text>
			</view>

			<view class="detail_describe_box">
				<view class="detail_describe">
					杜泊羊原产地南非，是世界著名的肉用羊品种。根据其头颈的颜色，分为白头杜泊和黑头杜泊两种。成年公羊和母羊的体重分别在120公斤和85公斤左右。虽然杜泊羊个体中等，但体躯丰满，体重较大。杜泊羊以产肥羔肉特别见长，胴体肉质细嫩、多汁、色鲜、瘦肉率高，被国际誉为“钻石级肉”。
				</view>
			</view>

			<view class="detail_price">
				<text style="color: #FF0000;font-size: 26rpx;margin-right: 10rpx;">￥258</text>
				<text style="color: #999999;font-size: 16rpx;text-decoration: line-through;">￥358</text>
			</view>

			<view class="detail_outline">
				<view class="detail_outline_left">
					<text class="detail_outline_top">公</text>
					<text class="detail_outline_bottom">性别</text>
				</view>
				<view class="detail_outline_partition"></view>
				<view class="detail_outline_mid">
					<text class="detail_outline_top">2020.06.06</text>
					<text class="detail_outline_bottom">出生日期</text>
				</view>
				<view class="detail_outline_partition"></view>
				<view class="detail_outline_right">
					<text class="detail_outline_top">50kg</text>
					<text class="detail_outline_bottom">体重</text>
				</view>
			</view>

			<view class="detailBottom_list_box">

				<view class="detailBottom_listBegin">
					<view class="detailBottom_listBegin_left">
						认养数量
					</view>
					<van-stepper value="1" integer button-size="38rpx" />
				</view>


				<view class="detailBottom_list" v-for="(item,index) in list" :key="index" @click="isshow(index)">
					<view class="detailBottom_list_left">
						<text>{{item.title}}</text>
						<image src="/static/img/inquiry.png" style="width: 18rpx;height: 18rpx;margin-left: 10rpx;"></image>
					</view>
					<view class="detailBottom_list_right">
						<view class="detailBottom_list_right_content" v-show="item.price">
							<text>￥{{ item.price ? item.price : '' }}</text> ({{ item.time ? item.time : '' }})
						</view>
						<van-icon name="arrow" />
					</view>
				</view>
			</view>

			<view class="detailBottom_imgBox">
				<image src="/static/img/details.png" style="width: 100%;"></image>
				<image src="/static/img/details.png" style="width: 100%;"></image>
				<image src="/static/img/details.png" style="width: 100%;"></image>
				<image src="/static/img/details.png" style="width: 100%;"></image>
			</view>
		</view>

		<view class="detailBottom">
			<view class="detailBottom_left">
				<view style="color: #FF0000;margin-right: 24rpx;font-size: 20rpx;">￥<text style="font-size: 32rpx;">510</text></view>
				<text style="font-size: 18rpx;margin-right: 8rpx;color: #666;">费用明细</text>
				<van-icon name="arrow-down" color="#666666" size="18rpx" />
			</view>

			<view class="detailBottom_right" @click="fixedshow">
				确认认领
			</view>
		</view>

		<!-- 管理费弹框 -->
		<view class="monthlyFee_box" v-show=show>
			<view class="monthlyFee_top" @click="showFalse"></view>
			<view class="monthlyFee_box_main">
				<view class="monthlyFee_title">
					月管理费及说明
				</view>
				<view class="monthlyFee_main">
					<view class="monthlyFee_list" v-for="(item,index) in monthlyFee_list" :key="index">
						<text style="margin-right: 5rpx;">{{item.id}}、</text>
						<text>{{item.content}}</text>
					</view>
				</view>
				<view class="monthlyFee_btn">
					完成
				</view>
			</view>

		</view>

		<!-- 确认认领弹框 -->
		<view class="fixedbox" v-show="inquiry" @click="fixedflase">
			<image src="/static/img/risk_bac.png" style="width: 640rpx;height: 708rpx;position: absolute;top: 255rpx;left: 50%;transform: translateX(-50%);"></image>
			<view class="risk_title">
				风险提示
			</view>
			<view class="risk_listbox">
				<view class="risk_list" v-for="(item,index) in risk_list" :key='index'>
					{{item.id}}{{item.content}}
				</view>
			</view>
			<view class="risk_btn" :style="{'backgroundColor':bacColor}" @click="go_payment(timeNum)">
				确认认领<text v-show="timeNum">（{{timeNum}}s）</text>
			</view>
		</view>

	</view>
</template>

<script>
	import {
		go_back01
	} from '../../utils/go_back.js'
	import { get , imgHead } from '../../utils/request.js'
	
	export default {
		data() {
			return {
				imgArr: [1, 2, 3, 4],
				num: 1,
				list: [{
						id: 1,
						title: "月管理费",
						price: "252",
						time: "六个月"
					},
					{
						id: 2,
						title: "参保及理赔情况"
					},
					{
						id: 3,
						title: "认购服务"
					}
				],
				show: false, //是否有管理费弹框
				monthlyFee_list: [{
						id: 1,
						content: '费用及说明费用及说明费用及说明费用及说明费用及说明费用'
					},
					{
						id: 2,
						content: '费用及说明费用及说明费用及说明费用及说明费用及说明费用'
					},
					{
						id: 3,
						content: '费用及说明费用及说明费用及说明费用及说明费用及说明费用'
					},
					{
						id: 4,
						content: '费用及说明费用及说明费用及说明费用及说明费用及说明费用'
					}
				],
				risk_list: [{
						id: '1',
						content: '养羊有风险，认领需谨慎'
					},
					{
						id: '2',
						content: '养羊有风险，认领需谨慎'
					},
					{
						id: '4',
						content: '养羊有风险，认领需谨慎'
					},
				],
				bacColor: '#C6C6C6', //确认按钮颜色
				timeNum: 3,
				inquiry: false, //是否有确认领养弹框
				data:[],//详情—接口数据,
				imgHead:'',
			}
		},
		methods: {
			swiperImg(e) {
				this.num = e.target.current + 1
			},
			go_back() {
				go_back01()
			},
			isshow(index) {
				if (index === 0) {
					this.show = true
				}
			},
			showFalse() {
				this.show = false
			},
			fixedshow() {
				this.inquiry = true

				let time = setInterval(() => {
					this.timeNum--
					if (this.timeNum == 0) {
						clearInterval(time)
						this.bacColor = '#FF6C00'
					}
				}, 1000)
			},
			go_payment(sure) { //确认认领
				console.log(sure)
				if (!sure) {
					uni.navigateTo({
						url: '/pagesA/payment/payment'
					})
				}
			},
			fixedflase() {

				if (this.timeNum <= 0) {
					this.inquiry = false
					this.bacColor = '#C6C6C6'
					this.timeNum = 3
				}
			}
		},
		onLoad(option) {
			console.log( option.id )
			let _this = this
			
			_this.imgHead = imgHead
			
			get( 'sheepDetails' , {id:option.id} , (res) => {
				console.log(res.data)
			} , (res) => {})
		}
	}
</script>

<style>
	@import url("./calimDetail.css");
</style>
