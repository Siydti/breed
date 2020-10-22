<template>
	<view class="howCalim">
		<view class="detailTop">
			<swiper style="height: 450rpx;" :autoplay="true" :interval="3000" :duration="1000" @change="swiperImg">
				<swiper-item v-for="(item,idnex) in imgArr" :key="index">
					<image style="width: 100%;height: 450rpx;" src="/static/img/detailImg.png" mode=""></image>
				</swiper-item>
			</swiper>
			<view class="back">
				<image style="width: 44rpx;height: 44rpx; margin-right: 11rpx;" src="/static/img/detailBack.png" @click="go_back"></image>
			</view>
			<view class="imgNum">
				<image style="width: 17rpx;height: 18rpx;" src="/static/img/imgIcon.png" ></image>
				<text style="font-size: 20rpx;">{{num}}/</text>
				<text style="font-size: 20rpx;">{{imgArr.length}}</text>
			</view>
		</view>

		<view class="detailBottom_box">
			<view class="detailBottom">

				<view class="detailBottom_title">
					<view class="detailBottom_title_left">
						杜泊羊
					</view>

					<view class="detailBottom_title_right">
						No.2563265
					</view>
				</view>

				<view class="detailBottom_description">
					杜泊羊原产地南非，是世界著名的肉用羊品种。根据其头颈的颜色，分为白头杜泊和黑头杜泊两种。成年公羊和母羊的体重分别在120公斤和85公斤左右。虽然杜泊羊个体中等，但体躯丰满，体重较大。杜泊羊以产肥羔肉特别见长，胴体肉质细嫩、多汁、色鲜、瘦肉率高，被国际誉为“钻石级肉”。
				</view>

				<view class="detailBottom_price">
					￥512 <text>x2</text>
				</view>

				<image class="detailBottom_partition" src="/static/img/partition.png" @click="go_growthDynamic"></image>

				<view class="detailBottom_list_box">

					<view class="detailBottom_list" v-for="(item,index) in detailBottom_list" :key="index" @click="isshow( index )">

						<view class="detailBottom_list_left">
							<text>{{item.title}}</text>
							<image src="/static/img/inquiry.png" style="width: 18rpx;height: 18rpx;margin-left: 10rpx;"></image>
						</view>

						<view class="detailBottom_list_right">
							<text>{{item.type}}</text>
							<van-icon name="arrow" style="color: #999;margin-left: 10rpx;" />
						</view>


					</view>

					<view class="detailBottom_elseList">
						<text class="detailBottom_list_left">其它信息</text>
						<text class="detailBottom_list_right">未阉割、未受孕</text>
					</view>


				</view>

				<view class="detailBottom_description">
					<image src="/static/img/details.png" style="width: 100%;"></image>
				</view>

			</view>
		</view>

		<!-- 底部按钮框 -->
		<view class="detailBottom_fiexd">
			<view class="detailBottom_fiexd_left" style="background-color: #FF6C00;" @click="go_property">
				转让交易
			</view>
			<view class="detailBottom_fiexd_right" style="background-color: #04C272;" @click="go_foodie">
				吃货交割
			</view>
		</view>


		<!-- 弹框 -->
		<view class="monthlyFee_box" v-show=show >
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
	
	</view>
</template>

<script>
	import {
		go_back01
	} from '../../utils/go_back.js'
	export default {
		data() {
			return {
				imgArr: [1, 2, 3, 4],
				num: 1,
				detailBottom_list: [{
					title: "月管理服务费详情",
					type: "已交至：2020.06.06"
				}, {
					title: "参保及理赔情况",
					type: "已参保"
				}],
				show: false, //是否有弹框
				monthlyFee_list:[
					{id:1,content:'费用及说明费用及说明费用及说明费用及说明费用及说明费用'},
					{id:2,content:'费用及说明费用及说明费用及说明费用及说明费用及说明费用'},
					{id:3,content:'费用及说明费用及说明费用及说明费用及说明费用及说明费用'},
					{id:4,content:'费用及说明费用及说明费用及说明费用及说明费用及说明费用'}
				]
			}
		},
		methods: {
			swiperImg(e) {
				this.num = e.target.current + 1
			},
			go_back() {
				go_back01()
			},
			isshow( index ) {
				if( index === 0 ) {
					uni.navigateTo({
						url:'../../pages/serviceCharge/serviceCharge'
					})
				}
			},
			showFalse() {
				this.show = false
			},
			go_growthDynamic() {
				console.log( 1 )
				uni.navigateTo({
					url:'../../pages/growthDynamic/growthDynamic'
				})
			},
			go_property() {
				uni.navigateTo({
					url:'/pages/property/property'
				})
			},
			go_foodie() {
				uni.navigateTo({
					url:'../../pages/foodie/foodie'
				})
			}
		}
	}
</script>

<style>
	@import url("./howCalim.css");
</style>
