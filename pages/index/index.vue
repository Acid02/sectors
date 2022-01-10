<template>
	<view class="ar-floor">
		<navigator url="../indexs/indexs">11</navigator>
		<view class="z-title" title="限量稀缺"></view>
		<view class="ar-floor__wrapper">
			<!-- 背景层 -->
			<view class="color ar-colorful-bg">
				<view class="color__content"></view>
				<view class="color-radius1" style="animation-play-state: running;"></view>
				<view class="color-radius2" style="animation-play-state: running;"></view>
				<view class="color__mask"></view>
			</view>
			<!-- 描述详情层 -->
			<view class="ar-floor__content">
				<view class="ar-floor__content-sku-img">
					<image :src="datalist[index].image" mode="heightFix"></image>
				</view>
				<view class="ar-floor__content-sku-info">
					<view class="sku-info-top">
						<view class="taro-text">
							{{datalist[index].name}}
						</view>
						<view class="try-btn">
							去看看
						</view>
					</view>
					<view class="sku-info-bottom">
						<view class="jo-price jo-price--number jo-price--large price">
							<text class="taro-text jo-price__yen">¥</text>
							<text class="taro-text jo-price__text--big">{{datalist[index].price.slice(0,2)}}</text>
							<text class="taro-text jo-price__text--small">{{datalist[index].price.slice(2)}}</text>
						</view>
						<view class="wenan"></view>
					</view>
				</view>
				<!-- 轮播层 -->
				<view class="turntable">
					<!-- 轮播组件 -->
					<siucat-sectors ref='sectors' @Chend='Chend'></siucat-sectors>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				datalist:[
						{
							image: "https://m.360buyimg.com/mobile/s300x300_jfs/t1/170948/25/3671/756019/600924e7E6e895689/30c25b9f688cd686.png!q80.png", 
							price: "51.18",
							name:"爱死坤坤了❤124",
						},
					    {
					        "image": "//m.360buyimg.com/babel/jfs/t19072/106/897521151/792959/d15657af/5aaf7d21N0b0efbed.png",
					        "name": "佳洁士牙膏美白热感美白去烟渍淡黄淡化牙垢美国配方超值装+热感便携装共544g(北美设计)(新老包装,随机发货)",
					        "price": "119.8"
					    },
					    {
					        "image": "//m.360buyimg.com/babel/jfs/t1/176558/31/13048/190209/60ba1dfaEedb6759f/be96865b27cced61.jpg!q50.jpg",
					        "name": "欧乐B漱口水牙龈专护系列 自愈小气泡漱口水 净澈护龈双支装 防牙龈出血 防敏护龈 清新口气 共950ml",
					        "price": "169.9"
					    },
					    {
					        "image": "//m.360buyimg.com/babel/jfs/t1/179597/12/5135/63169/60a7a513Eda02a850/d24d4a9345a289f0.jpg!q50.jpg",
					        "name": "周杰伦mojito同款SelvaRey嘻瑞24K椰子味朗姆酒莫吉托洋酒鸡尾酒原装进口单支 750ml",
					        "price": "388"
					    },
					    {
					        "image": "//m.360buyimg.com/babel/jfs/t1/190262/19/6446/83018/60b9c04dEf691e3a8/4f81ac4647b435eb.jpg!q50.jpg",
					        "name": "【段星星刘冠佑同款】KVK毒液拼接手链ins风潮简约个性2021手链小众设计高级感 V01042211",
					        "price": "420"
					    },
					    {
					        "image": "//m.360buyimg.com/babel/jfs/t1/157583/12/2863/220365/5ffe9924Ebe443f28/01ec575df2d91a81.jpg!q50.jpg",
					        "name": "中国工艺 小克投资金攒金卡 黄金9999投资金条 1g5g投资金砖 2021福字纪念金币 牛年生肖1g",
					        "price": "425.5"
					    },
					    {
					        "image": "//m.360buyimg.com/babel/jfs/t1/156741/29/15106/88677/6049acf2E6c31c0cc/8102bcb1f4790501.jpg!q50.jpg",
					        "name": "新秀丽拉杆箱Samsonite行李箱男女旅行箱进口登机箱CURV材质贝壳箱20英寸白色人类之子 CS2",
					        "price": "4879"
					    },
					    {
					        "image": "//m.360buyimg.com/babel/jfs/t1/177946/11/8242/284789/60bf3573E434d2577/99a33c88f186971a.jpg!q50.jpg",
					        "name": "心相印厨房纸巾 小黄人系列吸油吸水加厚抽取擦手纸 2层70抽*8包整箱销售 厨房好帮手",
					        "price": "39.9"
					    },
					    {
					        "image": "//m.360buyimg.com/babel/jfs/t1/171797/26/6991/169617/608a56f0Ea7035fe3/e73518c24cabc6fa.jpg!q50.jpg",
					        "name": "燕京啤酒 8度 U8小度酒 500ml*12听 冬奥定制罐",
					        "price": "95"
					    },
					    {
					        "image": "//m.360buyimg.com/babel/jfs/t1/133288/16/13589/532661/5f940cc3E0a18c968/8b77a2ac85cc827f.jpg!q50.jpg",
					        "name": "暴雪魔兽世界大酋长萨尔大型雕像手办 均码 图片色",
					        "price": "5499"
					    },
					    {
					        "image": "//m.360buyimg.com/babel/jfs/t1/173990/28/12977/138985/60ba0bdcE0f34de84/ceb2b93cbce70bec.jpg!q50.jpg",
					        "name": "周生生 黄金转运珠Charme宝贝文化祝福系列祥云 不含手绳92439C定价",
					        "price": "900"
					    },
					    {
					        "image": "//m.360buyimg.com/babel/jfs/t1/176303/33/13774/154469/60c004ddE11e235f4/0be598603023c96a.jpg!q50.jpg",
					        "name": "MERIMIES X Snoopy史努比 十周年联名经典泰国剑桥包M号 红色史努比 | Trickysun（国内现货）",
					        "price": "599"
					    },
				],
				index:0,
			}
		},
		created() {
			this.$nextTick(()=>{
				this.$refs.sectors.add(this.datalist)
			})
		},
		methods: {
			Chend(index){
				this.index = index
			}
		}
	}
</script>

<style>
	.ar-floor {
		width: 100%;
		min-height: 100vh;
		background-color: #1F0020;
	}
	
	.z-title {
		width: 100%;
		height: 51.75rpx;
		background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAu4AAAAuCAMAAABAtGxlAAAAtFBMVEUAAAD////////////n5+fm5ubm5ub////////o6Ojr6+v////s7Oz////////////////m5ubo6Ojm5ubo6Oj////////////9/f3n5+fn5+fm5ubn5+f////q6ur9/f3o6Oj////r6+v8/Pzo6Ojo6Ojm5ub////n5+fv7+/////9/f3n5+fo6Ojs7Ozn5+fp6env7+/////n5+fr6+vv7+/q6urp6enz8/Pm5ubp6enm5uaateu9AAAAO3RSTlMAFzJFRHe7FTjKik1TJCkOCu9lzTMELh5D3ZkiiAJ6PlMagDTEvREHqlxIE/PRlNaRbyzkoGabryXgtXMLrYAAAAoYSURBVHja7NvrVtpAEADgIdlc5JJwCQQIAspFpLSCra3tvP97dSc7KBsCAe2fnO73w7NGzUGd2ezMLmAYhlEqSyBdMIxPaTtkVGXjCX0cjatZjRSMXDK/OefFJyGQSIip49wvFvPvj9YTKptdrfa42H/yrSat/yCZ1chBmKNyXyMeGManoO7nDnO1ArKGFhZ79aR1d+SiZha8ft3fTUQdVDoRAASTML2xu+4CeD68EagkIPWbYBifkaBu6mAuFyTPT7BYC6QuZ4Z+ednBjOESIOz1uhGSxU4IUd/VU56o17eoCCKvRx4xYW98jEAduJhrBFIjEKgrzgz98uuTngJtuus6BnAw68l/wiPffNIAw/gIBzUrGGAuB6Sg4XAoghROQMeZsuXMyE2Y2RDfuQlA89mnybqDWUPAYwIk36zhjY9ZoWYMyPLjbIjF2iD1Yid7uRkEvh/DKptCXJJmOQKPAamBYXwIz6q/nAGSR4HKwJXmnZvvepx1UHNhZrQcR4gv60bD876M8M2AqtRmP6T+EB4ROdcGkP4EGP+lwJb6kIot6RlSXyrSlysaM0IVloP1WI/Z/QLlN8cZFttnRiREwpP2VwBuuEwHR0v3mJbuLh5JnJNlAZym/+7PlhRDqm9LARil1e3bUkONLVJR4wppQrEIlaUabCejTOevpcVZpH81twz4zplBBBeYvGpJ3LwKOOwFCR5p3d2crCDgnGaFdIFULKLGDVvqm52q8opt8gDkzpJ6t0DCiuTBBdocohyru8A9W6lOsdgKpLuZIEOuOuUwasy2yAbT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) center no-repeat;
		background-origin: content-box;
		background-size: 100%;
		padding-bottom: 26.496rpx;
		padding-top: 50.7838rpx;
	}
	
	.ar-floor__wrapper {
		position: relative;
		margin: 0 auto;
		width: 100%;
		height: 928rpx;
		overflow: hidden;
	}
	
	.ar-floor .ar-colorful-bg {
	    margin: 0 auto;
	    width: 90%;
	    height: 100%;
	    border-radius: 13.248rpx;
	    overflow: hidden;
	    transform: translateZ(0);
		position: relative;
		background-color: #6236cd;
	}
	.color__content{
		width: 100%;
		height: 100%;
		background: radial-gradient(circle 30rem at top left,#bffba3,transparent 50%),radial-gradient(circle 30rem at top right,#2fced5,transparent 50%),radial-gradient(circle 40rem at bottom left,#7241c4,transparent 50%);
		animation: hue 10s linear infinite;
	}
	.color-radius1{
		width: 300%;
		height: 300%;
		position: absolute;
		top: -150%;
		left: -150%;
		opacity: .5;
		background: radial-gradient(circle 30rem at top left,#bffba3,transparent 50%),radial-gradient(circle 30rem at top right,#2fced5,transparent 50%),radial-gradient(circle 40rem at bottom left,#7241c4,transparent 50%);
		animation: rotate 10s linear infinite;
		animation-play-state: paused;
	}
	.color-radius2{
		width: 300%;
		height: 300%;
		position: absolute;
		top: -150%;
		left: -150%;
		opacity: .8;
		background: radial-gradient(circle 50rem at top left,#bffba3,transparent 50%),radial-gradient(circle 50rem at top right,#7241c4,transparent 50%),radial-gradient(circle 40rem at bottom left,#2fced5,transparent 50%);
		animation: rotate 10s linear infinite reverse;
		animation-play-state: paused;
	}
	.color__mask{
		width: 100%;
		height: 100%;
		/* background: url('../../static/bg.png'); 小程序无法通过本地资源背景图 必须使用base64 或者网络图片 */
		 background: url(//m.360buyimg.com/babel/jfs/t1/177943/35/6821/338594/60b50503Ebc4501d6/b6026d01b3d81b06.png);
		background-size: 100%;
		opacity: .2;
		z-index: 10;
		position: absolute;
		left: 0;
		top: 0;
	}
	@keyframes hue{
		0% { filter: hue-rotate(0deg);}
		100% { filter: hue-rotate(360deg);}
	}
	@keyframes rotate{
		0% { transform: rotate(0);}
		100% { transform: rotate(360deg);}
	}
	
	.ar-floor__content {
	    position: absolute;
	    top: 0;
	    right: 0;
	    left: 0;
	    bottom: 0;
	    z-index: 99;
	}
	.ar-floor__content-sku-img {
		width: 300rpx;
		height: 300rpx;
		overflow: hidden;
		margin: 88.3202rpx auto;
		margin-bottom: 35.3282rpx;
	}
	.ar-floor__content-sku-img>image{
		height: 100%;
	}
	.ar-floor__content-sku-info{
		position: relative;
		margin: 0 66.24rpx;
		padding-bottom: 23.184rpx;
		display: flex;
		flex-direction: column;
		border-bottom: 1rpx solid rgba(230,230,230,.5);
		color: #FFFFFF;
	}
	.sku-info-top,.sku-info-bottom{
		display: flex;
		justify-content: space-between;
		
	}
	.sku-info-top>.taro-text{
		font-size: 30.9118rpx;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
	}
	.sku-info-top>.try-btn{
		margin-left: 30rpx;
		flex-shrink: 0;
		background-color: rgba(0, 0, 0, 0.6);
		display: flex;
		justify-content: center;
		width: 172.2188rpx;
		height: 64.0312rpx;
		line-height: 59.12rpx;
		font-size: 33.12rpx;
		border-radius: 200rpx;
	}
	.sku-info-bottom>.jo-price{
		padding: 0;
		font-size: 30rpx;
		line-height: 1;
	}
	.sku-info-bottom>.jo-price>.jo-price__yen,.sku-info-bottom>.jo-price>.jo-price__text--small{
		font-size:30.9092rpx;
	}
	.sku-info-bottom>.jo-price>.jo-price__text--big{
		font-size:48.5762rpx;
	}
	
	.wenan {
	    width: 167.7812rpx;
	    height: 9.90624rpx;
	    color: #fff;
	    background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJgAAAAJCAYAAADO+OXHAAACkElEQVRYhbVY7W3bMBB9KPpbWUBewF0gWiDqAPUEggdQM4DaAdwMEHiBeoHYA9QZIPYC1gL1AiwMvCsOB5IWSfsBhKUTdbz3jh8nwzn34ZxbOOdgWmOevTnnfnv6DarfR6BN8e+zNwF/K+dc5fEpcYbiGPjeytj/BGK0Mfna4gbahPy/Kp6vtNVmjJ72NkFjaVO0KOL2GdOxBdABqAGM6q0WwF7ZNgCOxus+YRwftM+acZwB/PT0fQFQ8Xrg2DveHwCsADQA1gDeaf/GvhL/lDg0t7pQm5nn+YVDz3iX5PrGOJfsM+e4W7ZUTNGiKO85E2zBJMoglUogOEgsSTmwPucUJhSnYKAA8m7D9kJR/wvBJPdXYg9xK9VmFnj+qJ6N9N1znEu/H5GFdg1TtSji9ikhoCNbq2xP/NVJrVXwTWQilGBGYVPxyP6hSVJx8oYQ4nYPbWryPCnbmuP0TPqcSb+nFkXcUnYwcdirgRvaNMGOTeOr2V5T0SlSX0g+Z9XK0elLiNgeIu/HuJVoIxjU8SQxPZv+33lU9txtck+LFC2yueVOsJary26T4Iqy9UDJ5AJXsfg4sl7IqetEkCqy6v9G3o9xK9HGV4PNeSwtzBE28r5TR1YOUrTI5pY6wUYmtuWWePY4PU+cULL1V8Yu99rH7kZ13buqJ9bm2RNjt4WqRozbLbSxdUzDo8zGeja/OUjRIpubTLDaUw/YxAt23MbrQNJ9vk6ewUcS6Hh9UMWlELp1/bZn69T9A7+cmgk7wjVuudqEcFK7Wwl84x4StcjiJhPMd34u4cdW1Ql2mwz52gRqpks98Yufy4KR9nvhmfH3bAL7NeXDNW652vj6XiD1jv2LIBWh/KZokc4N2PwDgNr/uH0p39EAAAAASUVORK5CYII=) center no-repeat;
	    background-size: 100%;
		margin-top: 37rpx;
	}
	.turntable{
		position: relative;
		width: 100%;
		overflow: hidden;
		/* height: 1000rpx; */
	}
</style>
