<template>
	<view class="ar-floor">
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
					<image :src="datalist[index].image" mode="aspectFill"></image>
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
					<sectors ref='sectors' @Chend='Chend'></sectors>
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
					{image: "https://tvax1.sinaimg.cn/large/0072Vf1pgy1foxkilshjxj31hc0u04hb.jpg", price: "91.28",name:"爱死坤坤了❤1"},
					{image: "https://tvax1.sinaimg.cn/large/0072Vf1pgy1foxkcxngm7j31hc0u04g4.jpg", price: "90.22",name:"爱死坤坤了❤2"},
					{image: "https://tvax4.sinaimg.cn/large/0072Vf1pgy1foxlo4q77mj31kw0w0kev.jpg", price: "56.46",name:"爱死坤坤了❤3"},
					{image: "https://tvax1.sinaimg.cn/large/0072Vf1pgy1foenqvqwvqj31hc0xc7aj.jpg", price: "76.94",name:"爱死坤坤了❤4"},
					{image: "https://tvax4.sinaimg.cn/large/0072Vf1pgy1foxk70rdinj31kw0w0b19.jpg", price: "3.06",name:"爱死坤坤了❤5"} ,
					{image: "https://tvax3.sinaimg.cn/large/0072Vf1pgy1foxk73gascj31hc0u07e1.jpg", price: "70.34",name:"爱死坤坤了❤6"},
					{image: "https://tvax1.sinaimg.cn/large/0072Vf1pgy1foxkcbupzhj31kw0w0x4l.jpg", price: "21.17",name:"爱死坤坤了❤7"},
					{image: "https://tvax4.sinaimg.cn/large/0072Vf1pgy1foxk456b0fj31hc0u0dxu.jpg", price: "73.20",name:"爱死坤坤了❤8"},
					{image: "https://tvax3.sinaimg.cn/large/0072Vf1pgy1fodqpglwr2j312w0rnx6p.jpg", price: "18.16",name:"爱死坤坤了❤9"},
					{image: "https://tvax4.sinaimg.cn/large/0072Vf1pgy1foxk41fsxtj31hc0u0k3f.jpg", price: "27.62",name:"爱死坤坤了❤0"},
					{image: "https://tvax2.sinaimg.cn/large/0072Vf1pgy1foxk3qdi4cj31kw0w0kh2.jpg", price: "27.62",name:"爱死坤坤了❤11"},
					{image: "https://tvax4.sinaimg.cn/large/0072Vf1pgy1foxk7k489xj31kw0w0e3a.jpg", price: "9.83",name:"爱死坤坤了❤12"} ,
					{image: "https://tvax1.sinaimg.cn/large/0072Vf1pgy1foxk3vlirwj31hc0u0dsq.jpg", price: "20.83",name:"爱死坤坤了❤13"},
					{image: "https://tvax4.sinaimg.cn/large/006ZFECEgy1fr1x6k4294j31hc0u0b29.jpg", price: "45.82",name:"爱死坤坤了❤14"},
					{image: "https://tvax4.sinaimg.cn/large/0072Vf1pgy1foxlom31vmj311s1hc4k5.jpg", price: "54.96",name:"爱死坤坤了❤15"},
					{image: "https://tvax1.sinaimg.cn/large/0072Vf1pgy1foxlhl2l61j31hc0u0ash.jpg", price: "72.18",name:"爱死坤坤了❤1"},
					{image: "https://tvax4.sinaimg.cn/large/0072Vf1pgy1foxkcf9mfnj31hc0u0h7p.jpg", price: "16.40",name:"爱死坤坤了❤24"},
					{image: "https://tvax4.sinaimg.cn/large/0072Vf1pgy1foxkd8fiqgj31hc0u0h3v.jpg", price: "25.81",name:"爱死坤坤了❤ewr"},
					{image: "https://tvax3.sinaimg.cn/large/0072Vf1pgy1foxkcs4066j31hc0u0wrj.jpg", price: "42.15",name:"爱死坤坤了❤34"},
					{image: "https://tvax2.sinaimg.cn/large/0072Vf1pgy1foxkfughl3j31hc0u0to8.jpg", price: "50.71",name:"爱死坤坤了❤124"},
					{image: "https://tvax1.sinaimg.cn/large/0072Vf1pgy1foxkbze3llj31hc0u01cc.jpg", price: "42.97",name:"爱死坤坤了❤124"},
					{image: "https://m.360buyimg.com/mobile/s300x300_jfs/t1/170948/25/3671/756019/600924e7E6e895689/30c25b9f688cd686.png!q80.png", price: "51.18",name:"爱死坤坤了❤124"},
					{image: "https://tvax3.sinaimg.cn/large/0072Vf1pgy1foxlo91kiwj31hc0u0k9u.jpg", price: "52.26",name:"爱死坤坤了❤234"},
					{image: "https://tvax4.sinaimg.cn/large/0072Vf1pgy1foxkc6qp2sj31hc0u0k1p.jpg", price: "48.09",name:"爱死坤坤了❤qwr"},
					{image: "https://tvax1.sinaimg.cn/large/0072Vf1pgy1foxlhftiaqj31kw0w0tun.jpg", price: "31.89",name:"爱死坤坤了❤qwr"},
					{image: "https://tvax4.sinaimg.cn/large/0072Vf1pgy1fodqpbkx8xj30xc0nke81.jpg", price: "21.11",name:"爱死坤坤了❤rq"},
					{image: "https://tvax1.sinaimg.cn/large/0072Vf1pgy1fodqo0e8fzj31hc0xcqv5.jpg", price: "85.61",name:"爱死坤坤了❤a"},
					{image: "https://tvax1.sinaimg.cn/large/0072Vf1pgy1foxk7froooj31kw0w0hd1.jpg", price: "20.26",name:"爱死坤坤了❤d"},
					{image: "https://tvax1.sinaimg.cn/large/0072Vf1pgy1fodqoi6wubj31hc0u0hdt.jpg", price: "23.47",name:"爱死坤坤了❤c"},
					{image: "https://tvax2.sinaimg.cn/large/0072Vf1pgy1foxlhlozlfj31hc0u07lb.jpg", price: "75.89",name:"爱死坤坤了❤v"},
					{image: "https://tvax2.sinaimg.cn/large/0072Vf1pgy1foxlhgd2lzj31hc0u0dvn.jpg", price: "45.00",name:"爱死坤坤了❤v"},
					{image: "https://tvax3.sinaimg.cn/large/0072Vf1pgy1foxkc2jnyej31hc0u04g2.jpg", price: "26.36",name:"爱死坤坤了❤b"},
					{image: "https://m.360buyimg.com/mobile/s300x300_jfs/t1/170948/25/3671/756019/600924e7E6e895689/30c25b9f688cd686.png!q80.png", price: "40.07",name:"爱死坤坤了❤sde"},
					{image: "https://tvax1.sinaimg.cn/large/0072Vf1pgy1foxkcej4drj31hc0u0anw.jpg", price: "45.31",name:"爱死坤坤了❤v"},
					{image: "https://tvax2.sinaimg.cn/large/0072Vf1pgy1fodqn00gq2j315o0tg7wh.jpg", price: "5.35",name:"爱死坤坤了❤b"} ,
					{image: "https://tvax2.sinaimg.cn/large/0072Vf1pgy1foxkg53bgcj31kw0w01fi.jpg", price: "44.07",name:"爱死坤坤了❤b"},
				],
				index:0,
			}
		},
		onLoad() {
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
		background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAu4AAAAuCAMAAABAtGxlAAAAtFBMVEUAAAD////////////n5+fm5ubm5ub////////o6Ojr6+v////s7Oz////////////////m5ubo6Ojm5ubo6Oj////////////9/f3n5+fn5+fm5ubn5+f////q6ur9/f3o6Oj////r6+v8/Pzo6Ojo6Ojm5ub////n5+fv7+/////9/f3n5+fo6Ojs7Ozn5+fp6env7+/////n5+fr6+vv7+/q6urp6enz8/Pm5ubp6enm5uaateu9AAAAO3RSTlMAFzJFRHe7FTjKik1TJCkOCu9lzTMELh5D3ZkiiAJ6PlMagDTEvREHqlxIE/PRlNaRbyzkoGabryXgtXMLrYAAAAoYSURBVHja7NvrVtpAEADgIdlc5JJwCQQIAspFpLSCra3tvP97dSc7KBsCAe2fnO73w7NGzUGd2ezMLmAYhlEqSyBdMIxPaTtkVGXjCX0cjatZjRSMXDK/OefFJyGQSIip49wvFvPvj9YTKptdrfa42H/yrSat/yCZ1chBmKNyXyMeGManoO7nDnO1ArKGFhZ79aR1d+SiZha8ft3fTUQdVDoRAASTML2xu+4CeD68EagkIPWbYBifkaBu6mAuFyTPT7BYC6QuZ4Z+ednBjOESIOz1uhGSxU4IUd/VU56o17eoCCKvRx4xYW98jEAduJhrBFIjEKgrzgz98uuTngJtuus6BnAw68l/wiPffNIAw/gIBzUrGGAuB6Sg4XAoghROQMeZsuXMyE2Y2RDfuQlA89mnybqDWUPAYwIk36zhjY9ZoWYMyPLjbIjF2iD1Yid7uRkEvh/DKptCXJJmOQKPAamBYXwIz6q/nAGSR4HKwJXmnZvvepx1UHNhZrQcR4gv60bD876M8M2AqtRmP6T+EB4ROdcGkP4EGP+lwJb6kIot6RlSXyrSlysaM0IVloP1WI/Z/QLlN8cZFttnRiREwpP2VwBuuEwHR0v3mJbuLh5JnJNlAZym/+7PlhRDqm9LARil1e3bUkONLVJR4wppQrEIlaUabCejTOevpcVZpH81twz4zplBBBeYvGpJ3LwKOOwFCR5p3d2crCDgnGaFdIFULKLGDVvqm52q8opt8gDkzpJ6t0DCiuTBBdocohyru8A9W6lOsdgKpLuZIEOuOuUwasy2yAbTIbLOEqD7vEIy57b8QhBf1Ot8oSM6mHoEaXYHZ3kVKQRy27Mk9f0PNonBKKuJLfUO/rGxGnvFk7s+I895UU67PbmmKs4cLMSZ8Xh02dnfekPdxCqyTVXusG6QfOPvGKvceq8s7gGVCKRJCMXTu6cSPz6YBHq2NAGjpDybhGpskYeDx/ktXMDleEqQrPoJ5uM4c7FY25NmTl6/Jnl5FNKrR7rZpGvV9Nx6ryzayTWNmduDpdyDRTwgoU1ME7OsZrbkQyqwpEbmaV6MK8eXNpJxT5wvP4cuubngxMwWM8TbZL3xyRreRSJVz1YGESpC6O3+s/S1XMOSAkj5tjQDo5RCm1TU2CIhkAeu1S6wRCVaIamfWq10QBI7IU3rhWinf3HcaHH2tawjjX9WlXGDxCA52Tm8jQo4B2VB3IPzuFJ/OPrDVPhpaJTRsy1NtEnsyi4kCFQASacGQ8w1BOkrXojW5hvUdQTmqwZBX0a9TIDqnJueaTrsZBJU95P6ClMjrTFT3IvUH3tc6zyDUULcadCWqPrcVszheJqqOFtAR2+zR4flJ15KACzdm4XrDjjUXdcdjU7vwbYxhwiCgOP/1/5lTYuPEBw937io0TpZRvkc9pHja7uQjGPwz3DfoMls50wPFt4RXiqhqnQsxJIn5b4QAv6czg0n9yZCCE6Xn+KtZE2PJzSBXNWLjA/2KcwBsxK65V1Crb2s9SWuaMzsO4ARKq4j3X+rzg8CuI0X2tSkH3KwD9cxIsIc8/GryBo4p47jhL0YinBvKrshwbvQt2CUzZ1NmtnNQ+46w2VQGaHSnp4/wc4uTaT9EYIhouthvide52e5I/zMgUjeechuNzdtcgdG2fi2ZGlHQ67tQkKCiouKOP/ejileoFojdy3EgeClt4s4jF9uOKWE9FLfE573ijkcFz9xIJJXdMeHiSzVuzXK5l+Eu0Clddl7OxwsxhtSESVJG1PbFqITTLhMiNK3um59EvCryHGPePJApAn3/8/f9s62OU0giONMBw8iPttaRUeJSkZaa5KJiWnv+3+vsne73B0pwSm+Y3+vAuYOX+wx+/RfmzszpoUAzfwx+Fzbcbi+HzKBVeiPZPBOD894kUjgvAuCoJRBX9gtBJtP2nE8dmZaxy1CVergQkvbj6qShYOckA7DWOXFz2N65eqqkev3dGCVwNXgJvXoc73JSyqESKd3thjPUYdkUlZL9zhUbR+NE5GmAwtjyrNvJ2ZWp/LQjaJilJM8S+eyaxekvs8EuDX6QBzB0n9W5CG3QY5+Jrkvvlr2dbs9S9vbz3pGmM2JyPZxgzJTqSVl3fk0AeLLesjvkVZiBnatWpsU+z6dpEbFz4vR3E3Hp7MQ8AAuM7WRpk0ERtuBhjVfkY+MJhZFqTXUaC2vVu75VtvAKd9N7KsDWzTr7hueDrUsDUI3bo6tdhluImgjjVvEEtJ2oJn3BWnq6AMUM0Ww2Q86DFORAyJWjVCXRzo6HvwrbBDjIdoKSP1UYEq7E+oYUMtO/cFDpY6JW8RaScMG4HJi5i4gpV6h0dN2/2emEiLCyb0I6VwunIJUDAYaU2Kmmr2Xk0pgTpVdtex59n1Sae7cANxKmso7hKsVuiyLNDvZ2EFb4L2SW4yvH6kExu/j9nB24rW26WOw0o/8gll4L0eLwl/Jm1fx824zPFSaO8s72klD8R5pO/Bl3vXJtIr5A9qnuVfFnQdZD81OKiJVrK0mm18SuEM91HPPaLb1IUspMtCXo/nyE1E2i/daSUNpNoWLFKmaxAz+5UhHfXkF20HO7BXMHA9RCnvtdpjqxGDgx9rk2H298ETfRh+LDX2Ff/X+sjS7lTQbvEH2i+n3l2EsNfSRE31+8zvAtqvZSyRWOfonvL3pA13I7iT4Agf3ZYBv8+5SmzDlgL4UEcT6gN68Wna536Dr9Castzv1QvLgjXbSaKwSaTuW6Efb2g43BTgM+jMaBF829xXcLRWkYCOS6j0LKae7CfpNvgQuoUBXvijtZr/QvNWyJxQymQhgazszPFaJqaBe20F2aWs7hEk6Lr3hJgxHcKuWxwGwUXaKr+vdQkoxR+dl0EHBHubYjSZw43RCZvPf6Ap5jrlzQZT5X0TRsAgcR7ZSr/OxuiNroX9/VS4QGuwIdoyoBy3WJyvBV3mx7+JED18oJ4dacCZs7sxtoCw7RZGJNQ116go7arR7bgvMoKtmF1hF0k74G3vQ9L7Zk1T0KvYd78b4VYpDeVHhOCfNmdv8bsfSScesStOrc7MUQHqneZTIFO/aM2bApmPSdkzAvGd0pKQiwrZICKYz+RERm6cLy+8ZchqRucnvdvyKIgwWqcDkzkL13Rkz5+If4f4k6xHvqE6akLZD5SEzRwubvlm+TFd+RFjjbQRPdmcaY1oItD1T1cnI+JyRXgt5JVEYrtUy9FcyOCjhFjP7iX4kuirvqgm5pt9MOCopbnhhaqjRdmhhXikWJVeHPpfXghmfhbcnk7a6y8CrN1xC4KUm8KWgtcOxKtOAaSnl4bui0CJYfTCOTz0CN469owSO31Soq3P2674+A6eecoDeA0BWgE++J7fpwLEq04DyD/R2XE/+IpEzTo25ijQCZp73QBsBodulEyngIJgI2HCUzjfrFdNrgB8ewzAMw7SNv6u69tJZqn1vAAAAAElFTkSuQmCC) center no-repeat;
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
		width: 100%;
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
