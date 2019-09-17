<template>
	<view class="activity">
		<!-- <view class="header">Header</view> -->
		<!-- <swiper :current="TabCur" duration="300" @change="swiperChange">
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
		</view> -->
		<view class="content" v-if="activityContent === 'spike'" >
			<spike></spike>
		</view>
		<view class="content" v-if="activityContent === 'group'" >
			<group></group>
		</view>
		<view class="content" v-if="activityContent === 'bargain'" >
			<bargain></bargain>
		</view>
		<view class="content" v-if="activityContent === 'trial'" >
			<trial></trial>
		</view>
		
		<view class="footer">
			<view class="icons">
				<view class="box" @tap="spike">
					<view class="icon-img">
						<image src="../../static/temp/spike-on.png" mode=""></image>
					</view>
					<view class="text">秒杀</view>
				</view>
				<view class="box" @tap="group">
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
		</view>
	</view>
</template>

<script>
import FooterTab from '@/components/footer-tab/footer-tab.vue';
import spike from './spike/spike.vue';
import group from './group/group.vue';
import bargain from './bargain/bargain.vue';
import trial from './trial/trial.vue';
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
				activityContent: 'bargain'
			}
		},
		components:{
			FooterTab,
			spike,
			group,
			bargain,
			trial
		},
		methods: {
			spike() {
				// uni.navigateTo({
				// 	url:'./spike/spike'
				// })
				this.activityContent = 'spike';
				console.log("秒杀");
			},
			group() {
				// uni.navigateTo({
				// 	url:'./group/group'
				// })
				this.activityContent = 'group';
				console.log("拼团");
			},
			bargain() {
				// uni.navigateTo({
				// 	url:'./bargain/bargain'
				// })
				this.activityContent = 'bargain';
				console.log("砍价");
			},
			trial() {
				// uni.navigateTo({
				// 	url:'./trial/trial'
				// })
				this.activityContent = 'trial';
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
		width: 100%;
		height: 100vh;
		background-color: #f3f3f3;
	}
	.content {
		width: 100%;
		height: 100%;
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
