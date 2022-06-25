<template>
	<view style="text-align: center;">
	
		 <view style="margin-left: 25%;margin-top: 5%;">
			 
			<canvas id="qrcode" canvas-id="qrcode" :style="{ width: `${size}px`, height: `${size}px` }"></canvas>
					 
		 </view>
		 <view style="">请用手机浏览器扫码观看</view>
	    
	</view>
</template>

<script>
	import uQRCode from '@/uni_modules/js_sdk/u-qrcode';
	
	export default {
		data() {
			return {
				title: 'Hello',
				id: '',
				url:'',
				size:200
			}
		},
		onLoad: function(option) {
			
			this.id = option.url
			this.url='https://newsaas.guangzhouzhuangxiu01.cn/api/xcx/index/vedio?url='+this.id
		    
			const ctx = uni.createCanvasContext('qrcode');
			    const uqrcode = new uQRCode(
			      {
			        text: this.url,
			        size: this.size
			      },
			      ctx
			    );
			    uqrcode.make();
			    uqrcode.draw();
				

		},
		methods: {
			copyConnection() {
				uni.setClipboardData({
					data: this.url,
					success: function() {
						// console.log(this)
					}
				})


			},
			back(){
				uni.navigateBack({
					delta: 1
				});
			},
		}
	}
</script>

<style>
</style>