<template>
	<view>
		<view class="banner">
			<image class="banner-img" :src="data.image"></image>
			<view class="banner-title">{{data.title}}</view>
		</view>
		<view class="article-meta">
			<text class="article-author">所念皆星河</text>
			<text class="article-text">发表于</text>
			<text class="article-time">{{data.time}}</text>
		</view>
		<view class="article-content">
			<text>{{data.content}}</text>
		</view>
	</view>
</template>


<script>
	export default {
		data(){
			return{
				data:{}
			}
		},
		onLoad:function(options){
			this.data = JSON.parse(options.news)
		}
	}
</script>

<style>
	.banner {
			height: 360rpx;
			overflow: hidden;
			position: relative;
			background-color: #ccc;
		}
	
		.banner-img {
			width: 100%;
		}
	
		.banner-title {
			max-height: 84rpx;
			overflow: hidden;
			position: absolute;
			left: 30rpx;
			bottom: 30rpx;
			width: 90%;
			font-size: 32rpx;
			font-weight: 400;
			line-height: 42rpx;
			color: white;
			z-index: 11;
		}
	
		.article-meta {
			padding: 20rpx 40rpx;
			display: flex;
			flex-direction: row;
			justify-content: flex-start;
			color: gray;
		}
	
		.article-text {
			font-size: 26rpx;
			line-height: 50rpx;
			margin: 0 20rpx;
		}
	
		.article-author,
		.article-time {
			font-size: 30rpx;
		}
	
		.article-content {
			padding: 0 30rpx;
			overflow: hidden;
			font-size: 30rpx;
			margin-bottom: 30rpx;
		}
</style>
