<template>
	<view class="content">
		<view
			style="width: 100%;border-bottom: 1px  solid #dcdcdc;height: 30px;background-color: #8f8f94;color:aliceblue;"
			class="parent">
			<view class="sport-son">有问题请及时联系作者反馈</view>

		</view>

		<view style="width: 100%;border-bottom: 1px  solid #dcdcdc;">

			<input class="uni-input" focus placeholder="请输入视频了链接"
				style="height: 50px;border: 0px solid red;margin-left: 10px;width: 69%;float: left;" v-model="url" />
			<button class="mini-btn" type="primary" size="mini" style="margin-top: 10px;" @click="click">开始解析</button>

		</view>

		<view style="width: 100%;margin-top: 10px;">

			<button class="mini-btn" type="primary" size="mini"
				style="width: 45%;margin-left: 4%;background-color: #07C160;float: left;" @click="copy">粘贴地址</button>
			<button class="mini-btn" type="primary" size="mini"
				style="width: 45%;margin-left: 4%;background-color: #dcdcdc;float: left;" @click="clear">清空地址</button>

		</view>


		<view style="width: 100%;margin-top: 10px;text-align: center;color:aliceblue" @click="say">

			<view
				style="width: 41%;margin-left: 4%;background:linear-gradient(90deg,#CB0E97 0%,#7533B2 100%); ;float: left;padding: 2%;">
				<view><span style="font-size: 15px;">赞赏</span></view>
				<view><span style="font-size: 10px;">支持作者 多多分享</span></view>
			</view>

			<view
				style="width: 41%;margin-left: 4%;background:linear-gradient(90deg,#048AF3 0%,#19B6BB 100%);float: left;padding: 2%;">
				<view><span style="font-size: 15px;">教程</span></view>
				<view><span style="font-size: 10px;">学习如何去水印</span></view>

			</view>

		</view>

		<view style="width: 100%;margin-top: 10px;text-align: center;color:aliceblue;" @click="say">

			<view style="width: 41%;margin-left: 4%;background-color: #1CBBB4;float: left;padding: 2%;">
				<view><span style="font-size: 15px;">教程</span></view>
				<view><span style="font-size: 10px;">学习如何去水印</span></view>

			</view>

			<view style="width: 41%;margin-left: 4%;background-color: #A5673F;float: left;padding: 2%;">
				<view><span style="font-size: 15px;">批量解析</span></view>
				<view><span style="font-size: 10px;">解析用户所有作品</span></view>

			</view>

		</view>

		<view style="width: 94%;margin-top: 10px;text-align: center;margin-left: 2%;background-color: #39B54A;">
			<view style="width: 100%;float: left;background-color: #39B54A;">
				<button type="primary"
					style="font-size: 10px;width: 100%;background-color: #39B54A;height: 40px;font-size: 14px;">视频教程点我关注公众号
					永久免费使用</button>
			</view>
		</view>

		<!-- <view style="margin-top: 10px;"><span style="font-size:10px;color: #8f8f94;">--------作者联系方式-------</span></view>
		<view style="width: 100%;margin-top: 10px;text-align: center;color:aliceblue;margin-left: -20px;">

			<view style="width: 41%;margin-left: 4%;float: left;padding: 2%;">
				<image style="width: 150px; height: 150px;" src="/static/wx.jpg" mode="aspectFit"></image>
				<view class="image-title" style="color: #07C160;">微信1</view>
			</view>

			<view style="width: 41%;margin-left: 4%;float: left;padding: 2%;">

				<image style="width: 150px; height: 150px;" src="/static/wx.jpg" mode="aspectFill"></image>
				<view class="image-title" style="color: #07C160;">微信2</view>
			</view>

		</view> -->




	</view>

</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				
				url: ''
			}
		},
		onLoad() {

		},
		methods: {
			click() {
				console.log(this.url);
				uni.navigateTo({
					url: 'jiexi?url=' + this.url,
					success(res) {
						 //console.log('成功啦',res);
						},
						fail(err) {
						//console.log('失败啦',err);
						}
						
				});
				
			

			},
			copy(){
				uni.setClipboardData({
					data: this.url,
					success: function() {
						// console.log(this)
					}
				})
			},
			clear() {
				this.url='';
				
				
			
			
			},
			say(){
				 uni.showToast({ //uni默认吐司
				
				    title: '扫码联系作者', //提示内容
				
				    duration: 500 //提示显示时间
				
				});
				
			},
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.parent {
		overflow: hidden;
	}

	.sport-son {

		-webkit-animation: 10s rowup linear infinite normal;
		animation: 10s rowup linear infinite normal;
		position: relative;
		float: right;
		margin-right: -100px;
	}

	@-webkit-keyframes rowup {
		0% {
			left: 0;
		}

		100% {
			left: -100%;
		}
	}

	@keyframes rowup {
		0% {
			left: 0;
		}

		100% {
			left: -100%;
		}
	}




	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
