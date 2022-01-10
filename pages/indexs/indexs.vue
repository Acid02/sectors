<template>
	<view class="body">
		<view class="tab" :class="[{active}]" @tap="active = !active">
			+
		</view>
		<view v-for="item in MaxNumber" :key='item' class="item" :style="{'--i':item,'--max-number':MaxNumber}">
		 <view class="a">
		 	{{item}}
		 </view>	
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				active:false,
				MaxNumber:20
			}
		},
		created() {
			// setInterval(()=>{
			// let random = ~~(Math.random() * 30)+1;
			// this.MaxNumber = random
			// // console.log(random)
			// },1)
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
.body{
	position: relative;
	display: flex;
	justify-content: center;
	align-items: center;
	background-color: yellow;
	min-height: 300rpx;
	
	.item{
		position: absolute;
		border-radius: 50%;
		height: 30px;
		width: 30px;
		background-color: #fff;
		vertical-align: middle;
		text-align: center;
		transform-origin: 150rpx;
		left: 220rpx;
		transform: rotate(0) translateX(120rpx);
		white-space: transform;
		transition: .5s calc(.1s * var(--i));
		.a{
			transform: rotate(calc(1turn / (var(--max-number)*-1) * var(--i)));
		}
	}
	.active~.item{
		// left: 60px;
		transform: rotate(calc(1turn / var(--max-number) * var(--i))) translateX(0);
	}
	.tab{
		position: absolute;
		// border-radius: 50%;
		height: 60px;
		width: 60px;
		background-color: #1F0020;
		z-index: 9;
	}
}
</style>
