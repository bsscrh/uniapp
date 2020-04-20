<template>
	<view class="page">
		<view class="search-block">
			<view class="search-ico-wapper">
				<image src="../../static/icos/search.png" class="search-ico"></image>
			</view>
			
			<input type="text" placeholder="搜索预告" maxlength="10" class="search-text" focus="">
		</view>
		
		<view class="movie-list page-block">
			<view class="movie-wapper" v-for="trailer in trailerList" :key="trailer.id">
				<image :src="trailer.cover" class="poster"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				trailerList:[
				{
					id:1,
					cover:"http://122.152.205.72:88/superhero/MARVEL/CaptainMarvel/cover.jpg",
					poster:"http://122.152.205.72:88/superhero/MARVEL/CaptainMarvel/poster.jpg",
					trailer:"http://122.152.205.72:88/superhero/MARVEL/CaptainMarvel/trailer.mp4",
					name:"恶灵骑士"
				},
				{
					id:2,
					cover:"http://122.152.205.72:88/superhero/xman/TheNewMutants/cover.jpg",
					poster:"http://122.152.205.72:88/superhero/xman/TheNewMutants/poster.jpg",
					trailer:"http://122.152.205.72:88/superhero/xman/TheNewMutants/trailer.mp4",
					name:"X战警：新变种人"
				}
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	@import url("search.css");
</style>
