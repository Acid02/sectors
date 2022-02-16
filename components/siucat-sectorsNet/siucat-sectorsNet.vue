<template>
		<view class="turntable" @touchstart='Start' @touchmove='Move' @touchend='Chend' v-if="swiperList.length>0">
			<view class="turntable-content" :style='{height:`${MaxContent}rpx`,transform: `rotateZ(${turnZ}deg)`,transition}'>
				<view class="turntable-item" 
				v-for="(item,index) in swiperList" 
				:style="{
					zIndex:itemStyle[index].zIndex,
					transform:`rotate(${index*10}deg) translate3d(-50%, 0px, 0px)`
				}" :key='index'>
					<view class="ar-floor__sku-item" 
					:style="{
						transform: itemStyle[index].transform,transition: `transform 0.2s ease-out 0s`}">
						<view class="taro-img" :style="{width:`${MaxWidth}rpx`,height:`${MaxWidth}rpx`}">
							<image class="taro-img__mode-widthfix" :src="item.image" mode="aspectFill"></image>
						</view>
						<view class="jo-price">
							<text class="taro-text jo-price__yen">¥</text>
							<text class="taro-text jo-price__text--big">{{item.price.slice(0,2)}}</text>
							<text class="taro-text jo-price__text--small">{{item.price.slice(2)}}</text>
						</view>
					</view>
				</view>
		</view>
		</view>
</template>

<script>
	export default {
		name:'SecTors',
		props: {
			swiperList: {
				type: Array,
				default: ()=>[]
			}
		},
		data() {
			return {
				moveClientX:0,//滑动下标
				startClientX:0,
				differenceClientX:0,
				turnZ:0,
				transition:'',
				taroimg:0,
				itemStyle: [],
				slideNote: {
					x: 0,
					y: 0
				},
				integer:0
			}
		},
		computed:{
			MaxWidth(){
				return 36/this.swiperList.length * 140;
			},
			MaxContent(){
				return 36 * 40 * (36/this.swiperList.length);
			}
		},
		created() {
			// this.$nextTick(()=>{
			// 	this.swiperList = this.Limit(this.swiperList);
			// 	this.swiperList.forEach((item, index) => {
			// 		this.itemStyle.push(this.getStyle(index))
			// 	})
			// })
		},
		methods: {
			// 计算样式
			getStyle(e) {
				if (e > this.swiperList.length / 2) {
					var right = this.swiperList.length - e
					return {
						transform: 'scale(' + (1 - right / 10) + ')',
						zIndex: 50 - right,
					}
				} else {
					return {
						transform: 'scale(' + (1 - e / 10) + ')',
						zIndex: 50 - e,
					}
				}
			},
			//插入值
			add(data){
				this.swiperList = this.Limit(data)
				// 计算swiper样式
				this.swiperList.forEach((item, index) => {
					this.itemStyle.push(this.getStyle(index))
				})
				console.log('222',this.itemStyle)
			},
			//按下
			Start(e){
				this.moveClientX =e.touches[0].pageX;
				this.transition = ``
				
				this.slideNote.x = e.changedTouches[0] ? e.changedTouches[0].pageX : 0;
				this.slideNote.y = e.changedTouches[0] ? e.changedTouches[0].pageY : 0;
			},
			//滑动
			Move(e){
				var newList = JSON.parse(JSON.stringify(this.itemStyle));
				this.startClientX = this.moveClientX;
				this.moveClientX = e.changedTouches[0].pageX;
				this.differenceClientX = this.moveClientX - this.startClientX;
				// 这里可以改 滑动间距  *.1 值越大滑动间距越大
				let trZ = Math.abs(this.differenceClientX)*.1;
				if(this.differenceClientX>0){
					this.turnZ+=trZ
				}else{
					this.turnZ-=trZ
				}
				let integer = ~~(this.turnZ.toFixed())
				let sumTage = Math.abs(integer%10)
				// console.log('前',this.integer)
				if(sumTage<5){
					integer = integer > 0 ? integer - sumTage :  integer + sumTage
				}else{
					integer = integer > 0 ? integer + (10 - sumTage) :  integer - (10 - sumTage)
				}
				// 每次旋转时发生变化
				if(this.integer != integer){
					if(this.differenceClientX>0){
						newList.push(newList[0])
						newList.splice(0, 1)
					}else{
						let last = [newList.pop()]
							newList = last.concat(newList)
					}
					this.itemStyle = newList
				}
				this.integer = integer

			},
			//松开
			Chend(){
				// 归位
				this.transition = `transform 0.2s ease-out 0s`
				this.turnZ = this.integer;
				// console.log(this.turnZ)
				// 返回下标
				this.taroimg  = Math.abs(this.integer) / 10 % this.swiperList.length;
				if(this.integer > 0){
					this.taroimg = this.swiperList.length - this.taroimg
				}
				// console.log(this.taroimg)
				// this.$emit('Chend',this.taroimg)
			},
			//计算长度自动补全、截取
			Limit(arr){
				let leng = arr.length;
				if(leng == 36) return arr;
				let num = Math.abs(36 - leng);
				if(leng < 36){
					for(let i = 0;i < num;i++){
						let random = ~~(Math.random()*arr.length)
						arr.push(arr[random])
					}
					return arr
				}else{
					return arr.splice(0,36)
				}
			},
		}
	}
</script>

<style scoped>
.turntable {
	-webkit-touch-callout: none;
	user-select: none;
	padding-top: 30rpx;
    position: relative;
    width: 100%;
    overflow: hidden;
}
.turntable-content{
	height: 1600rpx;
	transform: rotateZ(0deg);
	will-change: transform;
}
.turntable-item{
	position: absolute;
	height: inherit;
	left: 50%;
	top: 0;
	transform: translate3d(-50%, 0px, 0px);
	-webkit-transform-origin: left center;
	-ms-transform-origin: left center;
	transform-origin: left center;
	-ms-touch-action: pan-y;
	touch-action: pan-y;
}
.ar-floor__sku-item{
	display: inline-block;
	padding: 6rpx 8rpx 0;
	box-shadow: 0.04704rem 0.16405rem 0.61867rem 0 rgb(49 29 87 / 41%);
	border-radius: 5px;
	background-color: #ebebeb;
	transform: translateZ(0);
	will-change: transform;
	overflow: hidden;
}
.taro-img {
	width: 140rpx;
	height: 140rpx;
	border-radius: 2rpx;
	background-color: #fff;
	padding: 2rpx;
	box-sizing: border-box;
	transform: translateZ(0);
	overflow: hidden;
}
.taro-img>image{
	width: 100%;
	height: 100%;
	border-style: none;
	pointer-events: none;
	background: 0 0;
	border: 0;
	margin: 0;
	outline: 0;
	padding: 0;
	vertical-align: bottom;
	/* object-fit: cover; */
}
.jo-price{
	text-align: center;
	padding:10rpx 0;
	font-size: 24rpx;
	font-family: JDZH-Regular,PingFangSC-Medium,-apple-system,Helvetica,"Microsoft YaHei",Arial,sans-serif,"微软雅黑","黑体","宋体",Helvetica,Verdana;
}
.jo-price__text--big{
	font-size: 36rpx;
}
</style>
