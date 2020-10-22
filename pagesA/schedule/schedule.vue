<template>
	<view class="schedule">
		<view class="schedule_msg">
			<van-icon name="notes-o" size='34rpx' />
			<text>订单信息</text>
		</view>

		<view class="schedule_list">
			<view class="schedule_list_box" v-for="(item,index) in listdata" :key="index">
				<text class="schedule_list_left">{{item.left}}</text>
				<text class="schedule_list_right">{{item.right}}</text>
			</view>
		</view>

		<!-- 进度条盒子 -->
		<view class="schedule_flow">
			<view class="van_steps_box">
			<van-steps :steps="steps" :active="active" active-color="#38D86E" inactive-color="#C3F3D3" />
			</view>
		</view>
			<view class="lookmore">
				查看详情
			</view>

		<view class="schedule_dispose">
			<view class="schedule_dispose-title">
				<image src="/static/img/ICON/lookmore.png" style="margin-right: 10rpx;width: 30rpx;height: 34rpx;"></image>
				<text>处理进度</text>
			</view>
			
			<view class="schedule_dispose_content">
				<view class="schedule_dispose_list">
					<image src="/static/img/ICON/right.png" style="margin-right: 20rpx;width: 35rpx;height: 35rpx;"></image>
					<view class="schedule_dispose_list_right">
						<view class="schedule_dispose_list_right_top">
							已经接收宰割申请，正在宰割中
						</view>
						<view class="schedule_dispose_list_right_bottom">
							2020.07.07 10:29
						</view>
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
				listdata: [{
						left: '订单号',
						right: '12345678954'
					},
					{
						left: '屠宰时间',
						right: '2020.07.07'
					},
					{
						left: '宰割数量',
						right: '2'
					},
					{
						left: '包装方式',
						right: '精品包装'
					},
					{
						left: '冷藏方式',
						right: '冷冻'
					}
				],
				steps: [{ //进度配置列表
						text: '宰割',
					},
					{
						text: '已宰割',
					},
					{
						text: '运输中',
					},
					{
						text: '已完成',
					},
				],
				active: 0, //步骤条位置
			}
		},
		methods: {

		}
	}
</script>

<style>
	@import url("./schedule.css");
</style>
