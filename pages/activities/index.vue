<template>
	<view class="activities">
		<uni-list v-for="(item,index) in actData" :key="index">
			<un-list>
				<view class="actWindon" >
					<text>{{item.breeds[0].name}}</text>
					<view>
						<image :src="item.url" alt="">
						<image :src="item.url" alt="">
						<image :src="item.url" alt="">
					</view>
				</view>
			</un-list>
		</uni-list>
		
		
	</view>
</template>

<script>
	export default{
		data(){
			return {
				actData:[]
			}
		},
		mounted() {
			uni.request({
				url:"https://api.thecatapi.com/v1/images/search?limit=8&size=full&breed_id=amis",
				success: (res) => {
					this.actData=res.data
					console.log(res.data);
				}
			})
		}
	}
</script>

<style>
	.actWindon view{
		display: flex;
		
	}
	.actWindon  text{
		padding: 20rpx;
	}
	.actWindon view image{
		width: 210rpx;
		height: 155rpx;
		padding: 20rpx;
		border-radius: 7%;
	}
</style>