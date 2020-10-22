<template>
	<view class="content">
		<image style="width: 100%;height: 402rpx;" :src="imgHead+data.index_banner"></image>
		<view class="logo">
			<view class="logoImg">
				<image style="width: 181rpx;height: 181rpx;" :src="imgHead+data.logo" mode=""></image>
			</view>
			<view class="introduce">
				{{ data.brief }}
			</view>
		</view>
		<view class="problem">
			<view class="someProblem">
				<text class="answer">难题解答</text>
				<image style="width: 345rpx;height: 300rpx;" src="../../static/img/index/problem.png" mode=""></image>
				<view class="fastLook">
					立即查看
				</view>
			</view>
			<view class="right">
				<view class="howCalim">
					<text class="calim">怎么认领？</text>
					<image style="width: 345rpx;height: 146rpx;" src="../../static/img/index/how.png" mode=""></image>
					<view class="fastLookSc">
						立即查看
					</view>
				</view>
				<view class="howSell">
					<text class="sell">怎么出售？</text>
					<image style="width: 345rpx;height: 146rpx;" src="../../static/img/index/sell.png" mode=""></image>
					<view class="fastLookrd">
						立即查看
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import { get , imgHead } from '../../utils/request.js'
	
	export default {
		data() {
			return {
				data:{},//首页接口数据
				imgHead:'',
			}
		},
		onLoad() {
			let _this = this

			_this.imgHead = imgHead
			get( 'index' , '' , (res) => {
				console.log( res )
				
				_this.data = res.data
				
				console.log( imgHead + _this.data.index_banner )
			} , ( res ) => {} )
			
		},
		methods: {

		}
	}
</script>

<style scoped>
	@import url("./index.css");
</style>
