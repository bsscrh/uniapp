<template>
	<view class="page">
		<!-- 轮播图start -->
		<swiper :indicator-dots="true" :autoplay="true" class="carousel">
			<swiper-item>
				<image src="../../static/carousel/batmanvssuperman.png" class="carousel"></image>
			</swiper-item>
			<swiper-item>
				<image src="../../static/carousel/spiderman.png" class="carousel"></image>
			</swiper-item>
		</swiper>
		<!-- 轮播图end -->

		<!-- 热门超英start -->
		<view class="page-block super-hot">
			<view class="hot-title-wapper">
				<image src="../../static/icos/hot.png" class="hot-ico"></image>
				<view class="hot-title">
					热门超英
				</view>
			</view>
		</view>

		<scroll-view scroll-x="true" class="page-block hot">
			<view class="single-poster">
				<view class="poster-wapper">
					<image src="../../static/poster/civilwar.jpg" class="poster"></image>
					<view class="movie-name">
						蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠
					</view>
					<view class="movie-score-wapper">
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-gray.png" class="star-ico"></image>
						<view class="movie-score">
							9.1
						</view>
					</view>
				</view>
			</view>
			
			<view class="single-poster">
				<view class="poster-wapper">
					<image src="../../static/poster/civilwar.jpg" class="poster"></image>
					<view class="movie-name">
						蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠
					</view>
					<view class="movie-score-wapper">
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-gray.png" class="star-ico"></image>
						<view class="movie-score">
							9.1
						</view>
					</view>
				</view>
			</view>
			
			<view class="single-poster">
				<view class="poster-wapper">
					<image src="../../static/poster/civilwar.jpg" class="poster"></image>
					<view class="movie-name">
						蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠
					</view>
					<view class="movie-score-wapper">
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-gray.png" class="star-ico"></image>
						<view class="movie-score">
							9.1
						</view>
					</view>
				</view>
			</view>
			
			<view class="single-poster">
				<view class="poster-wapper">
					<image src="../../static/poster/civilwar.jpg" class="poster"></image>
					<view class="movie-name">
						蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠
					</view>
					<view class="movie-score-wapper">
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-yellow.png" class="star-ico"></image>
						<image src="../../static/icos/star-gray.png" class="star-ico"></image>
						<view class="movie-score">
							9.1
						</view>
					</view>
				</view>
			</view>
		</scroll-view>
		<!-- 热门超英end -->
	</view>
</template>

<script>
	import common from "../../common/common.js";

	export default {
		data() {
			return {

			}
		},
		onLoad() {
			var serverUrl = common.serverUrl;
			var serverUrl2 = common.serverUrl2;
			// 在main.js里挂载
			var serverUrl3 = this.serverUrl3;
			console.log(serverUrl)
			console.log(serverUrl2)
			console.log(serverUrl3)
		},
		methods: {

		}
	}
</script>

<style>
	@import url("index.css");
</style>
