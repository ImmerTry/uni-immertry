<template>
	<div>
		<wuc-tab 
		:tab-list="tabList" 
		textFlex 
		:tabCur.sync="TabCur" 
		tab-class="text-center text-black bg-red" 
		select-class="text-orange"></wuc-tab>
		<swiper
			:current="TabCur"
			class="swiper"
			duration="300"
			:circular="true"
			@change="swiperChange3"
		>
		
		<!-- indicator-color="#ff0018"
		indicator-active-color="rgba(255,255,255,0)" -->
			<swiper-item v-for="(item, index) in tabList" :key="index">
				<div class="bg-white padding margin text-center text-black">{{ item.name }}</div>
			</swiper-item>
		</swiper>
	</div>
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
			TabCur: 0
		};
	},

	components: { WucTab },

	computed: {},

	methods: {
		tabChange(index) {
			this.TabCur = index;
		},
		tabChange2(index) {
			this.TabCur2 = index;
		},
		swiperChange2(e) {
			let { current } = e.target;
			this.TabCur2 = current;
		},
		swiperChange3(e) {
			let { current } = e.target;
			this.TabCur3 = current;
		},
		swiperChange4(e) {
			let { current } = e.target;
			this.TabCur4 = current;
		},
		swiperChange5(e) {
			this.TabCur5 = e.target.current;
		}
	},

	onReady() {}
};
</script>
<style lang="less" scoped></style>
