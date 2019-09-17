<template>
	<view class="content">
		<wuc-tab
		:tab-list="tabList" 
		:tabCur.sync="TabCur"
		:useFormat="useFormat"
		tabClass="bg-red"
		select-class="text-orange"></wuc-tab>
		<view class="group-contnet">
			<view class="timeGroup">
				<view class="title">拼团中，先拼先得哦！</view>
				<view class="timer">剩余时间</view>
			</view>
			<swiper
				:current="TabCur"
				class="swiper"
				duration="300"
				:circular="true"
				@change="swiperChange"
			>
				<swiper-item>
					<view class="spike-list">
						<view class="item" v-for="(item,itemIndex) in groupList" :key="itemIndex">
							<view class="item-info" @tap="toGoods(item)">
								<view class="img">
									<image :src="item.img"></image>
								</view>
								<view class="info">
									<view class="title">{{ item.title }}</view>
									<view class="discount">
										<view class="discount-content">
											{{ item.discount }}
										</view>
									</view>
									<view class="info-footer">
										<view class="amount">
											<view class="oldAmount">￥{{ item.oldAmount }}</view>
											<view class="newAmount">￥{{ item.newAmount }}</view>
										</view>
										<view class="sell">
											<view class="text">立即拼</view>
										</view>
									</view>
								</view>
							</view>
						</view>
					</view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import WucTab from '@/components/wuc-tab/wuc-tab.vue';
	export default {
		name:'group',
		data() {
			return {
				tabList:[
					{name:"正在拼团"},
					{name:'提前预知'},
				],
				useFormat:'onlyTitle',
				groupList: [
					{id:'1',title:'正品Dior/迪奥口红烈焰蓝金756#CD唇 膏夹心滋润哑光',img:'/static/temp/kouhong.png',discount:'旗舰店',oldAmount:'899.90',newAmount:'499.90'},
					{id:'2',title:'正品Dior/迪奥口红烈焰蓝金756#CD唇 膏夹心滋润哑光',img:'/static/temp/ping.png',discount:'旗舰店',oldAmount:'899.90',newAmount:'499.90'},
					{id:'3',title:'正品Dior/迪奥口红烈焰蓝金756#CD唇 膏夹心滋润哑光',img:'/static/temp/kouhong.png',discount:'旗舰店',oldAmount:'899.90',newAmount:'499.90'},
				],
			};
		},
		components: {
			WucTab
		},
		methods: {
			swiperChange(e) {
				let { current } = e.target;
				this.TabCur = current;
			}
		}
	}
</script>

<style lang="less" scoped>
	.content {
		width: 100%;
		height: 100%;
		swiper {
			width: 100%;
			height: 100vh;
		}
		.tabClass {
			background-color: red ;
		}
		.group-contnet {
			width: 92%;
			padding: 0 4%;
			.timeGroup {
				width: 92%;
				padding: 0 4%;
				height: 50rpx;
				font-size: 20rpx;
				display:flex;
				align-items: center;
				background-color: #FFFFFF;
				margin-top: -20rpx;
				border-radius: 5rpx;
				.title {
					width: 60%;
				}
				.timer {
					width: 40%;
				}
			}
			.spike-list {
				width: 100%;
				// height: 100%;
				.item {
					width: 100%;
					height: 100%;
					margin: 20rpx 0;
					// padding: 10rpx 0;
					display: flex;
					background-color:#FFFFFF;
					border-radius:10rpx;
					.item-info {
						width: 100%;
						height: 100%;
						display: flex;
						.img {
							width: 35%;
							height: 100%;
							border-radius: 10upx;
							flex-shrink: 0;
							image{
								width: 30vw;
								height: 30vw;
							}
						}
						.info{
							width: 65%;
							height: 100%;
							.title {
								width: 98%;
								font-size: 24rpx;
								padding-top: 20rpx;
							}
							.discount {
								width: 100%;
								font-size: 16rpx;
								color: #FFFFFF;
								display:flex;
								padding: 5rpx 0 20rpx 0;
								.discount-content {
									display:flex;
									justify-content:center;
									white-space: nowrap;
									border-radius: 5rpx;
									padding: 0 5rpx;
									background-color: #ff7200;
								}
							}
							.info-footer {
								width: 100%;
								height: 100%;
								display:flex;
								.amount {
									width:30%;
									height: 100%;
									.oldAmount {
										width: 100%;height: 100%;
										font-size: 22rpx;
										text-decoration: line-through;
										color: #9e9e9e;
										display:flex;
									}
									.newAmount {
										display:flex;
										width: 100%;height: 100%;
										font-size: 32rpx;
										color: #f30000;
									}
								}
								.sell {
									width:70%;
									height: 100%;
									.text {
										width: 40%;
										height: 40rpx;
										color: #FFFFFF;
										font-size: 27rpx;
										background-color: #ff0018;
										display: flex;
										justify-content: center;
										align-items: center;
										border-radius: 50rpx;
										float: right;
										margin-top: 25rpx;
										margin-right: 20rpx;
									}
								}
							}
						}
					}
				}
			}
		}
	}
</style>
