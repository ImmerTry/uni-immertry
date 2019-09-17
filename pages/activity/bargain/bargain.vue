<template>
	<view class="content">
		<view class="img">
			<image :src="bargainBg" mode=""></image>
		</view>
		
		<view class="spike-list">
			<view class="item" v-for="(item,itemIndex) in bargainNowList" :key="itemIndex">
				<view class="item-info" @tap="toGoods(item)">
					<view class="img">
						<image :src="item.img"></image>
					</view>
					<view class="info">
						<view class="title">{{ item.title }}</view>
						<view class="discount">
							
						</view>
						<view class="info-footer">
							<view class="amount">
								<view class="choppedAmount">已砍
									<text>{{ item.choppedAmount }}元</text>
								</view>
								<view class="timer">时间
									<text>23:23:23</text>
								</view>
							</view>
							<view class="sell">
								<view class="text">去砍价</view>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="spike-list">
			<view class="item" v-for="(item,itemIndex) in bargainList" :key="itemIndex">
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
								<view class="newAmount">砍低至
									<text>￥{{ item.newAmount }}</text>
								</view>
							</view>
							<view class="sell">
								<view class="text">去砍价</view>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:'bargain',
		data() {
			return {
				bargainBg:"/static/temp/bargain-bg.png",
				bargainList: [
					{id:'1',title:'正品Dior/迪奥口红烈焰蓝金756#CD唇 膏夹心滋润哑光',img:'/static/temp/kouhong.png',discount:'',oldAmount:'899.90',newAmount:'20'},
					{id:'2',title:'正品Dior/迪奥口红烈焰蓝金756#CD唇 膏夹心滋润哑光',img:'/static/temp/ping.png',discount:'1950人已参与',oldAmount:'899.90',newAmount:'20.90'},
				],
				bargainNowList:[
					{id:'1',title:'正品Dior/迪奥口红烈焰蓝金756#CD唇 膏夹心滋润哑光',img:'/static/temp/kouhong.png',discount:'',choppedAmount:'120'},
				]
			};
		},
		methods: {
			toGoods() {
				
			}
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
	.img {
		width: 100%;
		height: 100%;
		image{
			width: 100%;
			height: 200rpx;
		}
	}
	.spike-list {
		width: 96%;
		padding: 0 2%;
		.item {
			width: 100%;
			height: 100%;
			margin: 20rpx 0;
			// padding: 10rpx 0;
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
					}
				}
			}
		}
	}
}
</style>
