<template>
	<view>
		<scroll-view
		class="footer-tab"
		:class="tabClass" 
		:style="tabStyle"
		 scroll-with-animation 
		 scroll-x 
		 :scroll-left="scrollLeft"
		 >
		 <view class="footer-tab-item">
			<view class="item" 
			:class="[index === tabCur ? selectClass + ' cur':'']" 
			v-for="(item,index) in tabList"
			:key="index" :id="index" @tap="tabSelect(index,$event)">
				<view class="img">
					<image :src="item.img" mode=""></image>
				</view>
				<view class="name">{{ item.name }}</view>
			</view>
		</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		name: 'footer-tab',
		data() {
			return {
				
			};
		},
		props: {
			tabList: {
				type: Array,
				default () {
					return [];
				}
			},
			tabCur: {
			    type: Number,
			    default() {
			        return 0;
			    }
			},
			tabClass: {
			    type: String,
			    default() {
			        return '';
			    }
			},
			tabStyle: {
			    type: String,
			    default() {
			        return '';
			    }
			},
			selectClass: {
			    type: String,
			    default() {
			        return 'text-blue';
			    }
			}
		},
		mounted() {
			
		},
		methods:{
			tabSelect(index, e) {
			    if (this.currentTab === index) return false;
			    this.$emit('update:tabCur', index);
			    this.$emit('change', index);
			}
		},
		computed: {
			scrollLeft() {
			    return (this.tabCur - 1) * 60;
			}
		}
	}
</script>

<style lang="less" scoped>
.footer-tab {
	width:100%;
	height:100%;
	.footer-tab-item {
		display: flex;
		height: 80upx;
		width: 100%;
		justify-content: space-between;
		flex-wrap: wrap;
		.item {
			width: 80upx;
			height: 80upx;;
			display: flex;
			justify-content: center;
			flex-wrap: wrap;
			border:1rpx solid red;
			.img {
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
			.name {
				display: flex;
				justify-content: center;
				width: 100%;
				font-size: 22upx;
				color: #666;
			}
		}
		
	}
	.bg-red {
		background-color: #ff0018;
	}
}
</style>
