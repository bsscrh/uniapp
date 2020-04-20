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
			<view class="single-poster" v-for="superhero in hotSuperheroList" :key="'superhero'+superhero.id+10">
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

		<!-- 热门预告 start -->
		<view class="page-block super-hot">
			<view class="hot-title-wapper">
				<image src="../../static/icos/interest.png" class="hot-ico"></image>
				<view class="hot-title">
					热门预告
				</view>
			</view>
		</view>

		<view class="hot-movies page-block">

			<video v-for="(trailer,index) in hotTrailerList" :id="'hero'+trailer.id" :data-playingindex="trailer.id" @play="meIsPlaying"
			 :src="trailer.trailer" :poster="trailer.poster" class="hot-movie-single" controls :key="index+15"></video>

		</view>
		<!-- 热门预告 end -->
		<!-- 猜你喜欢 start -->
		<view class="page-block super-hot">
			<view class="hot-title-wapper">
				<image src="../../static/icos/guess-u-like.png" class="hot-ico"></image>
				<view class="hot-title">
					猜你喜欢
				</view>
			</view>
		</view>

		<view class="page-block guess-u-like">

			<view class="single-like-movie" v-for="(guess,gIndex) in guessULikeList" :key="'guess'+guess.id">

				<navigator open-type="navigate" :url="'../movie/movie?trailerId=' + guess.id">
					<image :src="guess.cover" class="like-movie"></image>
				</navigator>

				<view class="movie-desc">
					<view class="movie-title">
						{{guess.name}}
					</view>
					<trailerStars :innerScore="9.1" showNum="0"></trailerStars>
					<view class="movie-info">
						{{guess.basicInfo}}
					</view>
					<view class="movie-info">
						{{guess.releaseDate}}
					</view>
				</view>

				<view class="movie-oper" :data-gIndex="gIndex" @click="praiseMe">
					<image src="../../static/icos/praise.png" class="praise-ico"></image>
					<view class="praise-me">
						点赞
					</view>

					<view :animation="animationDataArr[gIndex]" class="praise-me animation-opacity">
						+1
					</view>
				</view>
			</view>
		</view>
		<!-- 猜你喜欢 end -->

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
				//热门
				hotSuperheroList: [{
						id: 1,
						cover: "../../static/poster/civilwar.jpg",
						name: "civilwar",
						trailer: "http://122.152.205.72:88/superhero/MARVEL/IronMan3/trailer.mp4",
						score: 9.1
					},
					{
						id: 2,
						cover: "../../static/poster/justice.png",
						name: "justice",
						trailer: "http://122.152.205.72:88/superhero/MARVEL/Thor3/trailer.mp4",
						score: 7.9
					}
				],
				//预告片
				hotTrailerList: [{
					id: 1,
					trailer: "http://122.152.205.72:88/superhero/MARVEL/Thor3/trailer.mp4",
					poster: "http://122.152.205.72:88/superhero/MARVEL/Thor3/cover.jpg"
				}, {
					id: 2,
					trailer: "http://122.152.205.72:88/superhero/MARVEL/IronMan3/trailer.mp4",
					poster: "http://122.152.205.72:88/superhero/MARVEL/IronMan3/cover.jpg"
				}],
				guessULikeList: [],
				animationData: {},
				animationDataArr: [{}, {}, {}, {}, {}],
				hello: "hello,这是组件传值测试~"
			}
		},
		onUnload() {
			// 页面卸载的时候，清除动画数据
			this.animationData = {};
			this.animationDataArr = [{}, {}, {}, {}, {}];
		},
		onLoad() {
			var serverUrl = common.serverUrl;
			var serverUrl2 = common.serverUrl2;
			// 在main.js里挂载
			var serverUrl3 = this.serverUrl3;
			console.log(serverUrl)
			console.log(serverUrl2)
			console.log(serverUrl3)

			// #ifdef APP-PLUS || MP-WEIXIN
			// 在页面创建的时候，创建一个临时动画对象
			this.animation = uni.createAnimation();
			// #endif

			this.getGuessULikeList();


		},
		onPullDownRefresh() {
			uni.showLoading({
				// 是否显示透明蒙层，防止触摸穿透
				mask: true
			});
			// uni.showNavigationBarLoading();
			this.getGuessULikeList();
			setTimeout(function(){
				uni.hideLoading();
				uni.stopPullDownRefresh();
			},1000);
			
		},
		methods: {
			getGuessULikeList() {
				var guessULikeList = [{
					id: 1,
					cover: "../../static/poster/civilwar.jpg",
					name: "蝙蝠侠大战超人1",
					basicInfo: "2018 / 美国 / 科幻 动作",
					releaseDate: "本·阿弗莱克 / 亨利·卡维尔 / 艾米·亚当斯 / 盖尔·加朵"
				}, {
					id: 2,
					cover: "../../static/poster/justice.png",
					name: "蝙蝠侠大战超人2",
					basicInfo: "2018 / 美国 / 科幻 动作",
					releaseDate: "本·阿弗莱克 / 亨利·卡维尔 / 艾米·亚当斯 / 盖尔·加朵"
				}, {
					id: 3,
					cover: "../../static/poster/justice.png",
					name: "蝙蝠侠大战超人3",
					basicInfo: "2018 / 美国 / 科幻 动作",
					releaseDate: "本·阿弗莱克 / 亨利·卡维尔 / 艾米·亚当斯 / 盖尔·加朵"
				}];
				var result = [];
				var ranNum = 2;
				for (var i = 0; i < ranNum; i++) {
					var ran = Math.floor(Math.random() * guessULikeList.length);
					//arr.splice(ran, 1)[0]返回被删除的元素，比如ran=8，打印arr.splice(ran, 1)=[80],打印arr.splice(ran, 1)[0]=80,打印arr=[0, 10, 20, 30, 40, 50, 60, 70, 90]
					result.push(guessULikeList.splice(ran, 1)[0]);
				};
				this.guessULikeList = result;
			},
			praiseMe(e) {
				// #ifdef APP-PLUS || MP-WEIXIN
				var gIndex = e.currentTarget.dataset.gindex;
				console.log(gIndex);
				this.animation.translateY(-60).opacity(1).step({
					duration: 400
				});

				// 导出动画数据到view组件，实现组件的动画效果
				// this.animationData = this.animation.export();
				//用animationData来承载一下动画，不然可能会报错，原因不是很清楚
				this.animationData = this.animation;
				this.animationDataArr[gIndex] = this.animationData.export();

				setTimeout(function() {
					this.animation.translateY(0).opacity(0).step({
						duration: 0
					});
					this.animationData = this.animation;
					this.animationDataArr[gIndex] = this.animationData.export();
				}.bind(this), 500)
				// #endif
			}
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
