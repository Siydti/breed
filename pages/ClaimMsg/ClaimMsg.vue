<template>
	<view class="ClaimMsg">

		<view class="ClaimMsg_box" v-for="(item,index) in ClaimMsg_list" :key="index" @click="go_details( item.titleType )">
			<view class="ClaimMsg_title" >
				<view class="ClaimMsg_title_left">
					<image src="/static/img/ClaimMsg_log.png" mode=""></image>
					{{item.title}}
				</view>

				<view class="ClaimMsg_title_right">
					{{ item.titleType ? item.titleType : ''}}
				</view>
			</view>

			<view class="ClaimMsg_main">
				<view class="ClaimMsg_main_left">
					<image src="/static/img/123.png"></image>
				</view>
				<view class="ClaimMsg_main_mid">
					<view> 编号：{{item.num}} </view>
					<view> 性别： {{item.sex}} </view>
					<view> 体重： {{item.weight}} </view>
					<view> 认领时间： {{item.time}} </view>
					<view> 缴费有限期： {{item.validity}} </view>
				</view>
				<view class="ClaimMsg_main_right">
					{{ item.price ? '￥'+item.price : '' }}
				</view>
			</view>

		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				ClaimMsg_list: [{
					id: 1,
					title: '波尔山羊',
					titleType: '宰割中',
					num: '23023146',
					sex: '公',
					weight: '53kg',
					time: '2020-06-06',
					validity: '2020.06.06-2020.07.06'
				}, {
					id: 2,
					title: '边区莱斯特羊',
					num: '23023146',
					sex: '公',
					weight: '53kg',
					time: '2020-06-06',
					validity: '2020.06.06-2020.07.06',
					price:'259'
				}]
			}
		},
		methods: {
			go_details(msg) {
				if( msg ){
					uni.navigateTo({
						 url: '/pagesA/schedule/schedule'
					})
				}else{
					uni.navigateTo({
						 url: '/pagesA/howCalim/howCalim'
					})
				}
			}
		}
	}
</script>

<style>
	@import url("./ClaimMsg.css");
</style>
