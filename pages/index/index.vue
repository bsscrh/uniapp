<template>
	<view class="page">
		<swiper :indicator-dots="true" :autoplay="true" class="carousel">
			<swiper-item>
				<image src="../../static/carousel/batmanvssuperman.png" class="carousel"></image>
			</swiper-item>
			<swiper-item>
				<image src="../../static/carousel/spiderman.png" class="carousel"></image>
			</swiper-item>
		</swiper>
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
