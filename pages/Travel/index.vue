<template>
	<view class="Travel">
		<view class="uni-margin-wrap travelTop">
			<swiper class="swiper" circular :indicator-dots="indicatorDots" previous-margin="50px" next-margin="50px" >
				<swiper-item >
					<view class="swiper-item"  >
						<image src="../../static/seaHome.jpeg" alt="">
					</view>
				</swiper-item>
				<swiper-item >
					<view class="swiper-item"  >
						<image src="../../static/seaHome.jpeg" alt="">
					</view>
				</swiper-item>
				<swiper-item >
					<view class="swiper-item"  >
						<image src="../../static/seaHome.jpeg" alt="">
					</view>
				</swiper-item>
			</swiper>
		</view>
		<view class="travelOptions">
			<view class="travelIcon">
				<image src="../../static/city.png" alt="">
				
			</view>
			<view>
				<image src="../../static/liqueur.png" alt="">
				
			</view>
			<view>
				<image src="../../static/classroom.png" alt="">
				
			</view>
			<view>
				<image src="../../static/application-effect.png" alt="">
				
			</view>
			
		</view>
		<view class="iconInfo">
			<text>酒店/娱乐</text>
			<text>餐饮/好物</text>
			<text>剧场/教育</text>
			<text>海滨城专区</text>
		</view>
		<view class="contentTitle">
			<text>—— 精选推荐 ——</text>
		</view>
		<view class="traevlContent">
			<uni-list v-for="(item,index) in traevlimage" :key="index">
				<uni-list   class="contentList">
					<view class="imageflexbox">
						<image :src="item.download_url" alt="">
					</view>
					<view class="describe">
						<text class="contitle">【都江堰|虹口】 择一处清心之地</text>
						<text class="titleDes">【都江堰|虹口】 择一处清心之地</text>
						<text class="price">￥249</text>
						<text class="afterPrice">￥328</text>
					</view>
				</uni-list>
			</uni-list>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				indicatorDots:false,
				autoplay:false,
				traevlimage:[]
			}
		},
		mounted() {
			uni.request({
				url:"https://picsum.photos/v2/list",
				method:"GET",
				success: (res)=> {
					console.log(res.data)
					this.traevlimage=res.data
				}
			})
		}
	}
</script>

<style>
	.Travel{
		background-color: #efefef;
	}
	.travelTop{
		text-align: center;

	}

	.travelTop image{
		width: 486rpx;
		height: 250rpx;
		margin: 0 10rpx;
		border-radius: 7%;
	}
	.travelOptions{
		display: flex;
		justify-content: space-around;

	}
	.travelOptions view{
		border-radius: 50%;
		width: 80rpx;
		height: 80rpx;
		display: flex;
		align-items: center;
		justify-content: center;
		
	}
	.travelOptions view image{
		width: 40rpx;
		height:40rpx;
	}
	.travelOptions view:nth-child(1){
		background-color: orange;
	}
	.travelOptions view:nth-child(2){
		background-color: skyblue;
	}
	.travelOptions view:nth-child(3){
		background-color: #9a7bff;
	}
	.travelOptions view:nth-child(4){
		background-color: #9cfeff;
	}
	.iconInfo{
		
		display: flex;
		justify-content: space-around;
		font-size: .5rem;
	}
	.contentTitle{
		text-align: center;
		padding: 20rpx;
		color: #959595;
	}
	.traevlContent{
		background-color: white;
	}
	.traevlContent view{
		width: 100%;
		height: 300rpx;

	}
	.traevlContent view image{
		width: 250rpx;
		height: 250rpx;
	}
	.contentList{
		display: flex;
		flex-direction: row;
	}
	.imageflexbox{
		display: flex;
		justify-content: space-evenly;
		align-items: center;
		}
		.describe{
			width: 400rpx;
			padding: 20rpx;
			display: flex;
			flex-direction: column;
			justify-content: space-evenly;
		}
		.describe text{
			white-space: nowrap;		
			overflow: hidden;
			text-overflow:ellipsis;
		}
		.contitle{
			font-size: 30rpx;
		}
		.titleDes{
			font-size: .5rem;
			color: #959595;
		}
		.price{
			color: red;
		}
		.afterPrice{
			text-decoration:line-through;
			font-size: .5rem;
			color: #959595;			
		}
</style>