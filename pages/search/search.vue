<template>
	<view class="page">
		<view class="search-block">
			<view class="search-ico-wapper">
				<image src="../../static/icos/search.png" class="search-ico"></image>
			</view>
			
			<input type="text" placeholder="搜索预告" maxlength="10" class="search-text" confirm-type="search" @confirm="search">
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
				],
				trailerList2: [],//用来保存trailerList
				keywords: '', //搜索的关键字
				page: 1, //当前第几页
				totalPage: 1 //总页数
			}
		},
		methods: {
			search(e) {
				var searchValue = e.detail.value;
				this.keywords = searchValue;
				this.trailerList2 = this.trailerList;
				this.trailerList = [];
				this.getSearchList(this.keywords,1,2);
			},
			getSearchList(keywords,page,pageSize) {
				for(var i=0;i<this.trailerList2.length;i++) {
					if(keywords == this.trailerList2[i].name){
						this.trailerList[0] = this.trailerList2[i];
					}
				}
			},
		}
	}
</script>

<style>
	@import url("search.css");
</style>
