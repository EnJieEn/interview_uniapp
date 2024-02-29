<template>
	<view class="content">
		<!-- 轮播图 -->
		<view class="content_box">
			<swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval"
				:duration="duration">
				<swiper-item v-for="item in swiperArr">
					<view :class="item.class" class="swiper_item">{{item.laber}}</view>
				</swiper-item>
			</swiper>
		</view>

		<!-- 功能1-5 -->
		<view class="content_box_two">
			<view class="content_box_two_item" v-for="item in content_box_twoArr">
				<img :src="item.img" alt="" srcset="" class="content_box_two_item_img" />
				<text>{{item.laber}}</text>
			</view>
		</view>
		
		<!-- 功能A-J -->
		<view class="content_box_three">
			<view class="content_box_three_item" v-for="item in content_box_threeArr" @click="onItem(item.value)">
				<img :src="item.img" alt="" class="content_box_three_item_img" />
				<text>{{item.laber}}</text>
			</view>
		</view>

		<view class="popBox" v-if="popShow" @tap.stop="onpop">
			<view class="popBox_center">
				<view class="popBox_center_title">
					{{title}}
				</view>
				<view class="popBox_center_center">
					<view class="popBox_center_center_item" v-for="item in popBoxArr" @tap.stop="onpopItem(e)">
						<img :src="item.img" alt="" class="popBox_center_center_item_img" />
						<text>{{item.laber}}</text>
					</view>
				</view>
			</view>
		</view>


		<!-- 底部导航栏 -->
		<TabBar :current-page="0" v-if="TabBarShow" />
	</view>
</template>

<script>
	export default {
		data() {
			return {
				popShow: false,
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500,
				TabBarShow: true,
				swiperArr: [{
						laber: "A",
						class: "uni-bg-red"
					},
					{
						laber: "B",
						class: "uni-bg-green"
					},
					{
						laber: "C",
						class: "uni-bg-blue"
					}
				],
				content_box_twoArr: [{
					laber: "功能1",
					img: require('@/static/tabbar/me.png')
				}, {
					laber: "功能2",
					img: require('@/static/tabbar/me.png')
				}, {
					laber: "功能3",
					img: require('@/static/tabbar/me.png')
				}, {
					laber: "功能4",
					img: require('@/static/tabbar/me.png')
				}, {
					laber: "功能5",
					img: require('@/static/tabbar/me.png')
				}],
				content_box_threeArr: [{
						laber: "功能A",
						value: "A",
						img: require('@/static/tabbar/me.png')
					},
					{
						laber: "功能B",
						value: "B",
						img: require('@/static/tabbar/me.png')
					},
					{
						laber: "功能C",
						value: "C",
						img: require('@/static/tabbar/me.png')
					},
					{
						laber: "功能D",
						value: "D",
						img: require('@/static/tabbar/me.png')
					},
					{
						laber: "功能E",
						value: "E",
						img: require('@/static/tabbar/me.png')
					},
					{
						laber: "功能F",
						value: "F",
						img: require('@/static/tabbar/me.png')
					},
					{
						laber: "功能G",
						value: "G",
						img: require('@/static/tabbar/me.png')
					},
					{
						laber: "功能H",
						value: "H",
						img: require('@/static/tabbar/me.png')
					},
					{
						laber: "功能I",
						value: "I",
						img: require('@/static/tabbar/me.png')
					}, {
						laber: "功能J",
						value: "J",
						img: require('@/static/tabbar/me.png')
					},
					{
						laber: "",
						value: "",
						img: ''
					}, {
						laber: "",
						value: "",
						img: ''
					},
				],
				title: '',
				popBoxArr: [{
					laber: "功能1",
					img: require('@/static/tabbar/me.png')
				}, {
					laber: "功能2",
					img: require('@/static/tabbar/me.png')
				}, {
					laber: "功能3",
					img: require('@/static/tabbar/me.png')
				}, {
					laber: "功能4",
					img: require('@/static/tabbar/me.png')
				}, {
					laber: "功能5",
					img: require('@/static/tabbar/me.png')
				}, {
					laber: "功能6",
					img: require('@/static/tabbar/me.png')
				}, {
					laber: "功能7",
					img: require('@/static/tabbar/me.png')
				}, {
					laber: "功能8",
					img: require('@/static/tabbar/me.png')
				}, {
					laber: "功能9",
					img: require('@/static/tabbar/me.png')
				}, {
					laber: "功能10",
					img: require('@/static/tabbar/me.png')
				}]
			}
		},
		onLoad() {

		},
		methods: {
			changeIndicatorDots(e) {
				this.indicatorDots = !this.indicatorDots
			},
			changeAutoplay(e) {
				this.autoplay = !this.autoplay
			},
			intervalChange(e) {
				this.interval = e.target.value
			},
			durationChange(e) {
				this.duration = e.target.value
			},
			onItem(e) {
				console.log(e);
				this.title = '功能' + e
				this.popShow = !this.popShow
				this.TabBarShow = !this.TabBarShow
			},
			onpop() {
				this.popShow = !this.popShow
				this.TabBarShow = !this.TabBarShow
			},
			onpopItem(e) {
				console.log('处理事件！');

			}
		}
	}
</script>

<style>
	.popBox_center_center {
		display: flex;
		flex-wrap: wrap;
		background-color: #ffffff;
	}

	.popBox_center_title {
		height: 80rpx;
		text-align: center;
		color: #7ABC02;
		line-height: 80rpx;
	}

	.content_box_three_item {
		width: 25%;
	}

	.popBox_center {
		width: 96%;
		margin: 50% auto;
		border-radius: 20rpx;
		background-color: #272A3B;
	}

	.popBox {
		width: 100%;
		height: 100vh;
		position: fixed;
		top: 0rpx;
		left: 0rpx;
		background-color: #6F6F6F;
	}

	.content_box_three {
		width: 100%;
		display: flex;
		flex-wrap: wrap;
	}

	.popBox_center_center_item {
		padding: 20rpx;
		width: 25%;
		height: 180rpx;
		text-align: center;
		background-color: #ffffff;
		/* border: 1px solid #F0F0F0; */
	}

	.popBox_center_center_item_img {
		width: 80%;
		height: 80rpx;
	}

	.content_box_three_item {
		padding: 20rpx;
		width: 25%;
		height: 180rpx;
		text-align: center;
		background-color: #ffffff;
		border: 1px solid #F0F0F0;
	}

	.content_box_three_item_img {
		width: 80%;
		height: 80rpx;
	}

	.content_box_two {
		display: flex;
		width: 100%;
		background-color: #242424;
	}

	.content_box_two_item {
		flex: 1;
		/* border: 1px solid; */
		padding: 20rpx;
		text-align: center;
		color: #ffffff;
	}


	.content_box_two_item_img {
		width: 90%;
		height: 80rpx;
	}

	.content {

		width: 100%;
		/* height: 100vh; */
		background-color: #F2F2F2;
		height: 100vh;
	}

	.uni-bg-red {
		background-color: red;
	}

	.uni-bg-green {
		background-color: green;
	}

	.uni-bg-blue {
		background-color: blue;
	}

	.content_box {
		width: 100%;
		height: 273rpx;
		/* overflow: hidden; */
	}

	.swiper_item {
		height: 300rpx;
		text-align: center;
		line-height: 300rpx;
	}
</style>