<template>
	<view class="activity">
		<view class="header">Header</view>
		<swiper :current="TabCur" duration="300" @change="swiperChange">
		  <swiper-item v-for="(item,index) in tabList" :key="index">
			<div>{{item.name}}</div>
		  </swiper-item>
		</swiper>
		<view class="tabs">
			<footer-tab  
			:tab-list="tabList" 
			tab-class="bg-red" 
			:tabCur.sync="TabCur" 
			@change="tabChange">
			</footer-tab>
		</view>
		<!-- <view class="footer">
			<view class="icons">
				<view class="box" @tap="spike">
					<view class="icon-img">
						<image src="../../static/temp/spike.png" mode=""></image>
					</vie:class="tabClass" :style="tabStyle"w>
					<view class="text">秒杀</view>
				</view>
				<view class="box" @tap="toChat">
					<view class="icon-img">
						<image src="../../static/temp/group.png" mode=""></image>
					</view>
					<view class="text">拼团</view>
				</view>
				<view class="box" @tap="bargain">
					<view class="icon-img">
						<image src="../../static/temp/bargain.png" mode=""></image>
					</view>
					<view class="text">砍价</view>
				</view>
				<view class="box" @tap="trial">
					<view class="icon-img">
						<image src="../../static/temp/trial.png" mode=""></image>
					</view>
					<view class="text">试用</view>
				</view>
			</view>
		</view> -->
	</view>
</template>

<script>
import FooterTab from '@/components/footer-tab/footer-tab.vue';
	export default {
		data() {
			return {
				tabList:[
					{id:'1',name:'秒杀',img:'/static/temp/spike.png'},
					{id:'2',name:'拼团',img:'/static/temp/group.png'},
					{id:'3',name:'砍价',img:'/static/temp/bargain.png'},
					{id:'4',name:'试用',img:'/static/temp/trial.png'},
				],
				TabCur:0,
			}
		},
		components:{
			FooterTab
		},
		methods: {
			spike() {
				uni.navigateTo({
					url:'./spike/spike'
				})
				console.log("秒杀");
			},
			toChat() {
				uni.navigateTo({
					url:'./group/group'
				})
				console.log("拼团");
			},
			bargain() {
				uni.navigateTo({
					url:'./bargain/bargain'
				})
				console.log("砍价");
			},
			trial() {
				uni.navigateTo({
					url:'./trial/trial'
				})
				console.log("试用");
			},
			swiperChange(e) {
				this.TabCur = e.target.current;
			}
		}
	}
</script>

<style lang="less" scoped>
	.activity {
		background-color: #f3f3f3;
	}
	.tabs {
		position: fixed;
		bottom: 0upx;
		width: 92%;
		padding: 0 4%;
		height: 99upx;
		// display: flex;
		// align-items: center;
		border-top: solid 1upx #eee;
		
	}
	.footer {
		position: fixed;
		bottom: 0upx;
		width: 92%;
		padding: 0 4%;
		height: 99upx;
		border-top: solid 1upx #eee;
		background-color: #fff;
		z-index: 2;
		display: flex;
		// justify-content: space-between;
		align-items: center;

		.icons {
			display: flex;
			height: 80upx;
			width: 100%;
			justify-content: space-between;

			.box {
				width: 80upx;
				height: 80upx;
				display: flex;
				justify-content: center;
				flex-wrap: wrap;
				.icon-img {
					width: 100%;
					height: 40rpx;
					display: flex;
					image {
						width: 40rpx;
						height: 40rpx;
						padding: 0 20rpx;
						// justify-content: center;
						align-items: center;
					}
				}

				.text {
					display: flex;
					justify-content: center;
					width: 100%;
					font-size: 22upx;
					color: #666;
				}
			}
		}
	}
</style>
