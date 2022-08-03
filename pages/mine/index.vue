<template>
	<view class="mine">
		<view class="avatatLogin">
			<image src="../../static/user.png" alt="">
			<text>登录/注册</text>
		</view>
		<view class="orders">
			<view class="orderIcon">
				<image src='../../static/plan.png'>
				<image src='../../static/funds.png'>
				<image src='../../static/ticket.png'>
				<image src='../../static/order.png'>
			</view>
			<view class="order">
				<text>签到</text>
				<text>积分</text>
				<text>电子券</text>
				<text>订单</text>
			</view>
		</view>
		<uni-group mode="card" class="cardOptions">
			<uni-list :border="false">
				<image src="../../static/customer.png" alt="">
				<text>客服</text>
			</uni-list>
			<uni-list :border="true">
				<image src="../../static/ticket.png" alt="">
				<text>我的会员年卡</text>
			</uni-list>
			<uni-list :border="true">
				<image src="../../static/setting-two.png" alt="">
				<text>设置</text>
			</uni-list>
			
			<uni-list :border="false">
				<image src="../../static/rotate-one.png" alt="">
				<text>大转盘</text>
			</uni-list>
		</uni-group>
	</view>
</template>

<script>
</script>

<style>
	.mine{
		background-color: #e8e8e8;
	}
	.avatatLogin{
		display: flex;
		align-items: center;
		padding: 20rpx;
	}
	.avatatLogin image{
		width: 100rpx;
		height: 100rpx;
		border-radius: 50%;
		border: 1px solid #000;
		background-color: #eee;
	}
	.avatatLogin text{
		font-size: 1.5rem;
		text-indent: .5rem;
	}
	
	
	.orders{
		background-color: white;
		border-radius: 3%;
		margin: 20rpx;
		padding: 20rpx;
	}
	.orderIcon{
		display: flex;
		justify-content: space-around;
	}
	.orderIcon image{
		width: 60rpx;
		height: 60rpx;
	}
	.order{
		display: flex;
		justify-content: space-around;
		color: #4f4f4f;
	}
	.order text:nth-child(1){
		text-indent: 5rpx;
	}
	.order text:nth-child(2){
		text-indent: 15rpx;
	}
	.order text:nth-child(4){
		margin-right: 10rpx;
	}
	
	.cardOptions .uni-list{
		display: flex;
		flex-direction: row;
		padding: 10px;
		color:#4f4f4f;
	}
	.cardOptions image{
		width: 40rpx;
		height: 40rpx;
	}
	.cardOptions .uni-list text{
		text-indent: 1rem;
	}
</style>