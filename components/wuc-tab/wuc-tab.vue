<template>
  <scroll-view class="wuc-tab" :class="tabClass" :style="tabStyle" scroll-with-animation scroll-x :scroll-left="scrollLeft">
   <view v-if="useFormat === 'verticalTitle'">
      <view class="wuc-tab-item" :class="[index === tabCur ? selectClass + ' cur':'']" v-for="(item,index) in tabList" :key="index" :id="index" @tap="tabSelect(index,$event)">
        <view :class="item.icon"></view>
        <view class="time">{{ item.name }}</view>
		<view class="status">{{ item.status }}</view>
      </view>
    </view>

    <view class="flex text-center" v-if="useFormat === 'horizontalTitle'">
      <view class="wuc-tab-item flex-sub" :class="index === tabCur ? selectClass + ' cur':''" v-for="(item,index) in tabList" :key="index" :id="index" @tap="tabSelect(index,$event)">
        <view :class="item.icon"></view>
        <view class="time">{{item.name}}</view>
		<view class="status">{{ item.status }}</view>
      </view>
    </view>
	<view class="flex text-center" v-if="useFormat === 'onlyTitle'">
	  <view class="wuc-tab-item flex-sub" :class="index === tabCur ? selectClass + ' cur':''" v-for="(item,index) in tabList" :key="index" :id="index" @tap="tabSelect(index,$event)">
	    <view class="time">{{item.name}}</view>
	  </view>
	</view>
	</view>
  </scroll-view>
</template>
<script>
export default {
    name: 'wuc-tab',
    data() {
        return {
			title:''
		};
    },
    props: {
        tabList: {
            type: Array,
            default() {
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
        },
		useFormat: {
			type: String,
			default() {
			    return '';
			}
		}
    },
    methods: {
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
};
</script>
<style  scoped>
div,
scroll-view,
swiper {
	box-sizing: border-box;
}
.wuc-tab {
    white-space: nowrap;
}
.wuc-tab-item {
    height: 90upx;
    display: flex;
	flex-wrap: wrap;
    line-height: 90upx;
    margin: 0 10upx;
    padding: 0 20upx;
	opacity: 0.5;
}
.time {
	width: 100%;
	height: 50rpx;
	line-height: 50rpx;
	display: flex;
	font-size: 36rpx;
	align-items: center;
	justify-content: center;
	color: #FFFFFF;
}
.status {
	width: 100%;
	height: 20rpx;
	line-height: 20rpx;
	display: flex;
	flex-wrap: wrap;
	align-items: center;
	justify-content: center;
	font-size: 24rpx;
	color: #FFFFFF;
}
.wuc-tab-item.cur {
	/* border: 4rpx solid #FFFFFF; */
	/* border-bottom: 4rpx solid #FFFFFF; */
	opacity: 1;
}

.wuc-tab.fixed {
	position: fixed;
	width: 100%;
	top: 0;
	z-index: 1024;
	box-shadow: 0 1upx 6upx rgba(0, 0, 0, 0.1);
}

.flex {
    display: flex;
}
.text-center {
    text-align: center;
}
.flex-sub {
    flex: 1;
}
.text-blue{
  color:#0081ff;
}
.text-white{
  color:#ffffff;
}
.bg-white{
    background-color: #ffffff;
}
.bg-blue{
    background-color: #0081ff;
}
.bg-red {
	background-color: #ff0018;
}
.text-orange{
  color: #f37b1d
}

.text-xl {
	font-size: 36upx;
}

</style>

