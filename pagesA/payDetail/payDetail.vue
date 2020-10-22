<template>
	<!-- 交易明细 -->
	<view class="payDetail">
		<view class="payDetail_title">
			<view :class="{payDetail_title_type:'payDetail_title_type' , title_active : index == active ? 'title_active' : '' }" v-for="(item,index) in payDetail_title" :key="index" @click="activeTitle(index)">
				{{ item.title }}
				<view :class="{title_active_after : index == active ? 'title_active_after' : '' }"></view>
			</view>
		</view>
		
		<view class="payDetail_main">
			<view class="payDetail_list" v-for="(item,index) in payDetail_list" :key="index">
			
				<view class="payDetail_list_left">
					<view class="payDetail_list_left_money">
						{{item.type == "充值" ? '+' : '-'}}{{item.money}}
					</view>
					<view class="payDetail_list_left_type">
						{{item.type}}
					</view>
				</view>
			
				<view class="payDetail_list_right">
					<view class="payDetail_list_right_ucceed">
						{{item.ucceed}}
					</view>
					<view class="payDetail_list_right_time">
						{{item.time}}
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
				payDetail_title:[
					{ id:1 , title:"全部" },
					{ id:2 , title:"充值明细" },
					{ id:3 , title:"认养交易" },
					{ id:4 , title:"转让交易" },
					{ id:5 , title:"缴费明细" },
				],
				 payDetail_list: [{
				 		money: 1000,
				 		type: '提现',
				 		ucceed: '成功',
				 		time: '2020-01-06 02.13'
				 	},
				 	{
				 		money: 1000,
				 		type: '充值',
				 		ucceed: '成功',
				 		time: '2020-01-06 02.13'
				 	},
				 	{
				 		money: 1000,
				 		type: '认养交易',
				 		ucceed: '成功',
				 		time: '2020-01-06 02.13'
				 	},
				 	{
				 		money: 1000,
				 		type: '转让交易',
				 		ucceed: '成功',
				 		time: '2020-01-06 02.13'
				 	},
				 	{
				 		money: 500,
				 		type: '管理费',
				 		ucceed: '成功',
				 		time: '2020-01-06 02.13'
				 	}
				 ],
				active:0,//动态title 			
			}
		},
		methods: {
			activeTitle(index) {
				this.active = index
			}
		}
	}
</script>

<style>
@import url("./payDetail.css");
</style>
