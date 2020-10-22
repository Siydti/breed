<template>
	<view class="serviceCharge">
		<view class="serviceCharge_mainBox">
			
			<view class="serviceCharge_main_title">
				缴纳月管理费情况信息
			</view>
			
			<view class="main_list" v-for="(item,index) in main_list" :key="index">
				<view class="main_children" v-for="(items,indexs) in item" :key="indexs">{{items.td}}</view>
			</view>
		</view>
		
		<view class="serviceCharge_notice">
			（注：请仔细核对表中信息，如出现错误请联系工作人员。）
		</view>
		
		<image src="/static/img/close_btn.png" class="close_btn"></image>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				main_list:[
					[{td:'已交服务费情况'},{td:'已交费日期'},{td:'下次续费日期'}],
					[{td:'已交'},{td:'2020.06.06'},{td:'2020.12.06'}],
					[{td:'已交'},{td:'2020.06.06'},{td:'2020.12.06'}],
					[{td:'已交'},{td:'2020.06.06'},{td:'2020.12.06'}],
					[{td:'已交'},{td:'2020.06.06'},{td:'2020.12.06'}]
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style>
@import url("./serviceCharge.css");
</style>
