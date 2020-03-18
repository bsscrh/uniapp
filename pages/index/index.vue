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
			<view class="single-poster" v-for="superhero in hotSuperheroList" :key="superhero.id">
				<view class="poster-wapper">
					<image :src="superhero.cover" class="poster"></image>
					<view class="movie-name">
						{{superhero.name}}
					</view>

					<trailerStars :innerScore="superhero.score" showNum="1"></trailerStars>
				</view>
			</view>
		</scroll-view>
		<!-- 热门超英end -->
		<!-- <hello myval="hello,这是组件传值测试~~"></hello> -->
		<!-- <hello :myval="hello"></hello> -->
		
	</view>
</template>

<script>
	import common from "../../common/common.js";
	import hello from "../../components/hello.vue"
	import trailerStars from "../../components/trailerStars.vue"

	export default {
		data() {
			return {
				hotSuperheroList: [{
						id: 1,
						cover: "../../static/poster/civilwar.jpg",
						name: "civilwar",
						trailer: "http://122.152.205.72:88/superhero/MARVEL/IronMan3/trailer.mp4",
						score:9.1
					},
					{
						id: 2,
						cover: "../../static/poster/justice.png",
						name: "justice",
						trailer: "http://122.152.205.72:88/superhero/MARVEL/IronMan3/trailer.mp4",
						score:7.9
					}
				],
				hello:"hello,这是组件传值测试~"
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

		},
		components: {
			hello,
			trailerStars
		}
	}
</script>

<style>
	@import url("index.css");
</style>
