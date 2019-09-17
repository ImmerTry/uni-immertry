<template>
	<view class="content">
		<wuc-tab 
		:tab-list="tabList" 
		:useFormat="useFormat"
		:tabCur.sync="TabCur" 
		tab-class="text-center text-black bg-red" 
		select-class="text-orange"></wuc-tab>
		<swiper
			:current="TabCur"
			class="swiper"
			duration="300"
			:circular="true"
			@change="swiperChange"
		>
			<swiper-item v-for="(time, index) in timeList" :key="index">
				<view class="spike-list">
					<view class="item" v-for="(item,itemIndex) in spikeList" :key="itemIndex">
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
										<view class="now">正在秒杀</view>
										<view class="progress">已售75%</view>
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
			tabList: [
				{ name: '00:00', status: '已开抢' },
				{ name: '热抢好货', status: '好货快抢' },
				{ name: '08:00', status: '已开抢' },
				{ name: '10:00', status: '已开抢' },
				{ name: '11:00', status: '抢购进行中' },
				{ name: '12:00', status: '即将开场' },
				{ name: '13:00', status: '即将开场' },
				{ name: '14:00', status: '即将开场' },
				{ name: '15:00', status: '即将开场' },
				{ name: '17:00', status: '即将开场' },
				{ name: '19:00', status: '即将开场' },
				{ name: '21:00', status: '即将开场' },
				{ name: '22:00', status: '即将开场' },
				{ name: '23:00', status: '即将开场' }
			],
			timeList:[
				{ id: '1', status: '已开抢' },
				{ id: '2', status: '好货快抢' },
				{ id: '3', status: '已开抢' },
				{ id: '4', status: '已开抢' },
				{ id: '5', status: '抢购进行中' },
				{ id: '6', status: '即将开场' },
				{ id: '7', status: '即将开场' },
				{ id: '8', status: '即将开场' },
				{ id: '9', status: '即将开场' },
				{ id: '10', status: '即将开场' },
				{ id: '11', status: '即将开场' },
				{ id: '12', status: '即将开场' },
				{ id: '13', status: '即将开场' },
				{ id: '14', status: '即将开场' }
			],
			
			spikeList: [
				{id:'1',title:'正品Dior/迪奥口红烈焰蓝金756#CD唇 膏夹心滋润哑光',img:'/static/temp/kouhong.png',discount:'限量到手299元',oldAmount:'899.90',newAmount:'499.90'},
				{id:'2',title:'正品Dior/迪奥口红烈焰蓝金756#CD唇 膏夹心滋润哑光',img:'/static/temp/ping.png',discount:'限量到手299元',oldAmount:'899.90',newAmount:'499.90'},
				{id:'3',title:'正品Dior/迪奥口红烈焰蓝金756#CD唇 膏夹心滋润哑光',img:'/static/temp/kouhong.png',discount:'限量到手299元',oldAmount:'899.90',newAmount:'499.90'},
			],
			TabCur: 0,
			useFormat:'horizontalTitle'
		};
	},

	components: { WucTab },

	computed: {},

	methods: {
		tabChange(index) {
			this.TabCur = index;
		},
		
		swiperChange(e) {
			let { current } = e.target;
			this.TabCur = current;
		},
		
	},

	onReady() {}
};
</script>
<style lang="less" scoped>
	.content {
		width: 100%;
		height: 100%;
		swiper {
			width: 100%;
			height: 100%;
		}
	}
	.spike-list {
		width: 92%;
		padding: 0 4%;
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
							.now {
								width: 40%;
								height: 40rpx;
								color: #FFFFFF;
								background-color: #ff0018;
								font-size: 27rpx;
								border-radius: 50rpx;
								display: flex;
								justify-content: center;
								align-items: center;
								float: right;
								margin-right: 20rpx;
							}
							.progress {
								width: 100%;
								padding-top: 10rpx;
								// border: 1px solid red;
								height: 20rpx;
								display:flex;
								float: left;
								justify-content: center;
								color: #cccccc;
								font-size: 16rpx;
							}
						}
					}
				}
			}
		}
	}
</style>
