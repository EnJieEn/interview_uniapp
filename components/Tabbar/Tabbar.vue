<template>
	<view class="tabbar-container">
		<block>
			<view class="tabbar-item" v-for="(item,index) in tabbarList"
				:class="[item.centerItem ? ' center-item' : '']" @click="changeItem(item)">
				<view class="item-top">
					<!-- <image :src="currentItem==item.id?item.selectIcon:item.icon"></image> -->
					<img :src="item.icon" alt="" srcset="" />
				</view>
				<view class="item-bottom" :class="[currentItem==item.id ? 'item-active' : '']">
					<text>{{item.text}}</text>
				</view>
			</view>
		</block>

	</view>
</template>

<script>
	export default {
		props: {
			currentPage: {
				type: Number,
				default: 0
			}
		},
		data() {
			return {
				currentItem: 0,
				tabbarList: [{
					id: 0,
					path: "/pages/index/index",
					icon: require("@/static/tabbar/home.png"),
					selectIcon: require("@/static/tabbar/homeactive.png"),
					text: "首页",
					centerItem: false
				}, {
					id: 1,
					path: "/pages/index/index2",
					icon: require("@/static/tabbar/guanzhu.png"),
					selectIcon: require("@/static/tabbar/guanzhuactive.png"),
					text: "助手",
					centerItem: false
				}, {
					id: 2,
					path: "/pages/index/index3",
					icon: require("@/static/tabbar/add.png"),
					selectIcon: require("@/static/tabbar/addactive.png"),
					text: "常用",
					centerItem: true
				}, {
					id: 3,
					path: "/pages/index/index4",
					icon: require("@/static/tabbar/news.png"),
					selectIcon: require("@/static/tabbar/newsactive.png"),
					text: "分析",
					centerItem: false
				}, {
					id: 4,
					path: "/pages/index/index5",
					icon: require("@/static/tabbar/me.png"),
					selectIcon: require("@/static/tabbar/meactive.png"),
					text: "我的",
					centerItem: false
				}, ]

			};
		},
		mounted() {
			this.currentItem = this.currentPage;
			uni.hideTabBar();
		},
		methods: {
			changeItem(item) {
				let _this = this;
				//_this.currentItem = item.id;  
				uni.switchTab({
					url: item.path
				});
				// console.log(item.path)
			}
		}
	}
</script>
<style>
	view {
		padding: 0;
		margin: 0;
		box-sizing: border-box;
	}

	.tabbar-container {
		position: fixed;
		bottom: 0;
		left: 0;
		width: 100%;
		height: 110rpx;
		/* box-shadow: 0 0 5px #999;  */
		box-shadow: 0px 3px 20px rgba(0, 0, 0, 0.16);
		border-top: 1px;
		display: flex;
		align-items: center;
		padding: 5rpx 0;
		color: #999999;
		z-index: 200;
		background-color: #fff;
	}

	.tabbar-container .tabbar-item {
		width: 20%;
		height: 100rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		text-align: center;
	}

	.tabbar-container .item-active {
		color: #1AD080;
	}

	.tabbar-container .center-item {
		display: block;
		position: relative;
	}

	.tabbar-container .tabbar-item .item-top {
		width: 54rpx;
		height: 54rpx;
		padding: 0rpx;
	}

	.tabbar-container .center-item .item-top {
		flex-shrink: 0;
		width: 100rpx;
		height: 100rpx;
		position: absolute;
		top: -50rpx;
		left: calc(50% - 50rpx);
		border-radius: 50%;
		box-shadow: 0px 3px 20px rgba(0, 0, 0, 0.16);
		/* box-shadow: 0 0 5px #999;  */
		background-color: #ffffff;
		padding: 10rpx;
	}

	.tabbar-container .tabbar-item .item-top image {
		width: 100%;
		height: 100%;
	}

	tabbar-container .tabbar-item:nth-child(3) .item-top image {
		background: #ff0000;
	}

	.tabbar-container .tabbar-item .item-bottom {
		font-size: 28rpx;
		width: 100%;
	}

	.tabbar-container .center-item .item-bottom {
		position: absolute;
		bottom: 5rpx;
	}
</style>