<template>
	<view class="content">
		<!-- <view class="itemList">
			<view class="tabClass" v-for="(item,index) in tabList" :key="index">
				<view class="item">{{ item.name }}</view>
			</view>
		</view> -->
		<wuc-tab :tab-list="tabListByTitle" 
		 :tabCur.sync="TabCur"
		 :useFormat="useFormat"
		 select-class="text-orange">
		 </wuc-tab>
		<view class="img">
			<image :src="trialBg" mode=""></image>
		</view>
		<swiper :current="TabCur" class="swiper" duration="300" :circular="true" @change="swiperChange">
			<swiper-item v-for="(item,tabIndex) in trialList" :key="tabIndex">
				<view class="trialAll" v-if="tabIndex === 1">
					<view class="spike-list">
						<view class="item" v-for="(item,itemIndex) in trialList" :key="itemIndex">
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
											<view class="oldAmount">
												原价{{ item.oldAmount }}
											</view>
											<view class="newAmount">
												试用装
											</view>
										</view>
										<view class="sell">
											<view class="text">点击试用</view>
										</view>
									</view>
								</view>
							</view>
						</view>
					</view>
				</view>
				<view class="myTrial" v-else>
					<wuc-tab :tab-list="tabListByTrial"
					 :tabCur.sync="TabCur"
					 :useFormat="useFormat"
					 select-class="text-orange">
					 </wuc-tab>
					 <view class="spike-list">
					 	<view class="item" v-for="(item,trialIndex) in trialListBy" :key="trialIndex">
					 		<view class="item-info" @tap="toGoods(item)">
					 			<view class="img">
					 				<image :src="item.img"></image>
					 			</view>
					 			<view class="info">
					 				<view class="title">{{ item.title }}</view>
					 				<view class="info-footer">
										<view class="footer-timer">
											<view class="startTime">申请时间
												{{ item.startTime }}
											</view>
											<view class="endTime">剩余时间0天15小时25分</view>
										</view>
					 				</view>
					 			</view>
					 		</view>
					 	</view>
					 </view>
				</view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	import WucTab from '@/components/wuc-tab/wuc-tab.vue';
	export default {
		data() {
			return {
				trialBg:"/static/temp/trial-bg.png",
				trialList: [
					{id:'1',title:'正品Dior/迪奥口红烈焰蓝金756#CD唇 膏夹心滋润哑光',img:'/static/temp/kouhong.png',discount:'200人已参与试用',oldAmount:'899.90',newAmount:'499.90'},
					{id:'2',title:'正品Dior/迪奥口红烈焰蓝金756#CD唇 膏夹心滋润哑光',img:'/static/temp/ping.png',discount:'200人已参与试用',oldAmount:'899.90',newAmount:'499.90'},
				],
				tabListByTitle:[
					{name:'试用全部'},
					{name:'我的试用'}
				],
				tabListByTrial:[
					{name:'申请中'},
					{name:'申请成功'},
					{name:'申请失败'}
				],
				trialListBy:[
					{id:'1',title:'正品Dior/迪奥口红烈焰蓝金756#CD唇 膏夹心滋润哑光',img:'/static/temp/kouhong.png',startTime:'2019-09-17  17:02'},
					{id:'2',title:'正品Dior/迪奥口红烈焰蓝金756#CD唇 膏夹心滋润哑光',img:'/static/temp/ping.png',startTime:'2019-09-17  17:02'},
				],
				TabCur:0,
				useFormat:'onlyTitle'
			};
		},
		components: {
			WucTab
		}
	}
</script>

<style lang="less" scoped>
.content {
	width: 100%;
	height: 100%;
	background-color:#F3F3F3;
	swiper {
		width: 100%;
		height: 100vh;
	}
	
	.itemList {
		display: flex;
		width: 100%;
		height: 80rpx;
		.tabClass {
			width: 50%;
			display: flex;
			.item {
				display: flex;
				width: 100%;
				justify-content: center;
				align-items: center;
				font-size: 30rpx;
			}
			
		}
	}
	.img {
		width: 100%;
		height: 100%;
		image{
			width: 100%;
			height: 200rpx;
		}
	}
	.trialAll {
		
	}
	.myTrial {
		margin-top: 20rpx;
		width: 92%;
		background: orange;
		color: #000000;
		border-radius: 20rpx;
	}
	.spike-list {
		width: 92%;
		padding: 0 4%;
		.item {
			width: 100%;
			height: 100%;
			border-bottom: 1rpx solid #a3a3a3;
			display: flex;
			background-color:#FFFFFF;
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
						padding-top:20rpx;
						.amount {
							width:40%;
							height: 100%;
							.choppedAmount {
								width: 100%;
								height: 30rpx;
								font-size: 22rpx;
								display:flex;
								align-items: center;
								text {
									display: flex;
									padding-left: 5rpx;
									color: #ff2a00;
									font-size: 30rpx;
								}
							}
							.oldAmount {
								width: 100%;
								height: 30rpx;
								font-size: 20rpx;
								display:flex;
								align-items: center;
								color: #9e9e9e;
								text {
									width: 100%;
									color: #ff2a00;
									font-size: 30rpx;
								}
							}
							.timer {
								display:flex;
								width: 100%;
								height: 40rpx;
								font-size: 22rpx;
								align-items:center;
								text {
									display: flex;
									padding-left: 5rpx;
									color: #ff2a00;
									font-size: 16rpx;
								}
								
							}
							.newAmount {
								display:flex;
								width: 100%;
								height: 40rpx;
								font-size: 20rpx;
								color: #f30000;
								// justify-content:center;
								align-items:center;
								text {
									display: flex;
									color: #ff2a00;
									font-size: 30rpx;
								}
							}
						}
						.sell {
							width:60%;
							height: 80rpx;
							// border: 1rpx solid red;
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
								margin-top: 28rpx;
								margin-right: 20rpx;
							}
						}
						.footer-timer {
							display: flex;
							width: 100%;
							height: 90rpx;
							display: flex;
							flex-wrap: wrap;
							font-size:16rpx;
							.startTime {
								width: 100%;
								height: 60rpx;
								color: #9f9f9f;
								float: left;
								display: flex;
								align-items: flex-end;
								flex-wrap:wrap ;
								padding-left: 200rpx;
							}
							.endTime {
								// width: 100%;
								height: 30rpx;;
								color: #ff0018;
								display: flex;
								padding-left: 200rpx;
								// justify-content: flex-end;
								// align-items: center;
								flex-wrap:wrap ;
							}
						}
					}
				}
			}
		}
	}
}
</style>
