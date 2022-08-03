<template>
	<view class="container">
		<view class="top">
			<image src="../../static/top.jpg">
		</view>
		<view class="uni-margin-wrap">
			<swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval"
				:duration="duration" >
				<swiper-item v-for="(item,index) in imagePath" :key="index">
					<view class="swiper-item"  >
						<image :src="item.image_url" alt="">
					</view>
				</swiper-item>
			</swiper>
		</view>
		<view class="kind">
				<view class="flex-item "><image src='../../static/whale.png'><br/><text>海洋馆</text></view>
				<view class="flex-item "><image src='../../static/movie.png'><br/><text>电影</text></view>
				<view class="flex-item "><image src='../../static/skating.png'><br/><text>真冰场</text></view>
				<view class="flex-item "><image src='../../static/airplane.png'><br/><text>飞行学院</text></view>
				<view class="flex-item "><image src='../../static/plan.png'><br/><text>签到</text></view>
				<view class="flex-item "><image src='../../static/application.png'><br/><text>店铺</text></view>
				<view class="flex-item "><image src='../../static/coconut-tree.png'><br/><text>周边游</text></view>
				<view class="flex-item "><image src='../../static/parking.png'><br/><text>停车缴费</text></view>
				<view class="flex-item "><image src='../../static/finance.png'><br/><text>付款</text></view>
				<view class="flex-item "><image src='../../static/funds.png'><br/><text>积分</text></view>
		</view>
		<view class="hotEvent">
			<text class="headlines">头条 </text>
			<text class="headlinesContent"> 影城已全面恢复正常营业！</text>
		</view>
		<view class="hotMovie">
			<text class="hotMovieTitle">热映电影 </text><br/>
			<text class="headlinesContent">一起去看电影吧</text>
			<navigator url="navigate/navigate?title=navigate" hover-class="navigator-hover" class="more">
					<text>更多</text>
			</navigator>
		</view>
		<view class="movieTab">	
					<view class="uni-padding-wrap uni-common-mt">
						<uni-segmented-control :current="current" :values="items" :style-type="styleType"
							:active-color="activeColor" @clickItem="onClickItem" />
					</view>
					<view class="uni-margin-wrap movieSilde">
						<swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval"
							:duration="duration" >
							<swiper-item v-for="(item,index) in movieimage" :key="index">
								<view class="swiper-item"  >
									<image :src="item.image" alt="">
								</view>
							</swiper-item>
						</swiper>
					</view>
					<view class="content">
						<view v-if="current === 0">
							<scroll-view :scroll-x="true" :show-scrollbar="false" >
								<view class="newHotMovie" >
									<view v-for="(item,index) in movieimage" :key="index">
										<image :src="item.image" alt="">
									</view>
								</view>
							</scroll-view>
						</view>
						<view v-if="current === 1">
							<scroll-view :scroll-x="true" :show-scrollbar="false">
								<view class="newHotMovie" >
									<view v-for="(item,index) in movieimage" :key="index">
										<image :src="item.image" alt="">
									</view>
								</view>
							</scroll-view>
						</view>
					</view>	
		</view>
		<view class="hotMovie">
			<text class="hotMovieTitle">精品TOP10 </text><br/>
			<text class="headlinesContent">快把它们带走</text>
			<navigator url="navigate/navigate?title=navigate" hover-class="navigator-hover" class="more">
					<text>更多</text>
			</navigator>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				indicatorDots:true,
				autoplay:true,
				interval:3000,
				duration:500,
				imagePath:[],
				movieimage:[],
				
				items: ['滨海城4DMX激光影院', '蛟龙国际电影城'],
						styles: [{
								value: 'button',
								text: '按钮',
								checked: true
							},
							{
								value: 'text',
								text: '文字'
							}
						],		
				current: 0,
				colorIndex: 0,
				activeColor: '#b10b0b',
				styleType: 'text',
}
		},
		methods: {
			onClickItem(e) {
							if (this.current !== e.currentIndex) {
								this.current = e.currentIndex
							}
						},
						
							
		},
		mounted() {
			uni.request({
				method:"get",
				url:'https://api.juooo.com/home/index/getClassifyHome?city_id=0&abbreviation=&version=6.1.68&referer=2',
				success:(res)=>{
					//console.log(res.data.data.slide_list);
					this.imagePath=res.data.data.slide_list
				}
			}),
			uni.request({
				method:"get",
				url:'https://i.maoyan.com/api/mmdb/movie/v3/list/hot.json?ct=%E6%88%90%E9%83%BD&ci=59&channelId=4',
				success:(res)=>{
					//console.log(res.data.data.slide_list);
					this.movieimage=res.data.data.hot
				}
			})
		}
	}
</script>

<style>
	
	.container {
		font-size: 14px;
		line-height: 24px;
		
	}
	.top{
		width: 100%;
		display: flex;
		justify-content: center;
		background-color: #efefef;
		opacity: .9;
		position: fixed;
		left: 0;
		top: 0;
		z-index: 9;		
	}
	.top image{
		width: 200rpx;
		height: 100rpx;
	}
	uni-swiper {
	    margin-top: 50px;
		height: 200px;
		}
		uni-swiper image{
			width: 100%;
			height: 400rpx;
		}
		.kind{
			display: flex;
			justify-content: space-around;
			 flex-wrap: wrap;
			 padding-top: 10px;

		}
		.kind view{
			width: 15vw;
			text-align: center;
			padding: 5px;
		}
		.kind image{
			width: 80rpx;
			height: 80rpx;
		}
		.kind view text{
			display: block;
			margin-top: -10px;
			font-size: .5em;
		}
		.hotEvent{
			height: 30px;
			border-top: 1px solid #ccc;
			border-bottom: 1px solid #ccc;
			text-indent: 1rem;
		}
		.headlines{
			font-size: 15px;
			color: skyblue;
			font-weight: bold;	

		}
		.headlinesContent{
			opacity: .6;
			padding-left: .8rem;
		}
		
		.hotMovie{
			verticle-align:middle;
			text-indent: .8rem;
		}
		.hotMovieTitle{
			font-size: 20px;
			font-weight: bold;
		}
		.more{
			float: right;
			line-height: 2px;
			padding-right: 10px;
		}
		
		.segmented-control__item{
			width: 20px;
		}
		.movieSilde{
			margin-top: -50px;
			height: 200px;
			
		}
		.newHotMovie{
			display:flex;
			flex-wrap: nowrap
		}
		.newHotMovie image{
			width: 25vw;
			height: 20vh;
			padding: .5rem;
		}
		
	
</style>
