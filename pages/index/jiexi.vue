<template>
	<view class="">
		<view class="uni-padding-wrap uni-common-mt" style="width: 100%;border:0px solid red">
			<view style="width: 100%;border:0px solid red">
				<video id="myVideo" :src="url" :danmu-list="danmuList" enable-danmu danmu-btn controls
					style="width: 100%;border:0px solid red"></video>
			</view>
		</view>

		<view style="width: 100%;margin-top: 10px;">

			<button class="mini-btn" type="primary" size="mini"
				style="width: 45%;margin-left: 4%;background-color: #F37B1D;float: left;"
				@click="copyConnection">复制无水印链接</button>
			<button class="mini-btn" type="primary" size="mini"
				style="width: 45%;margin-left: 4%;background-color: #39B54A;float: left;" @click="click">保存到手机</button>

		</view>
		<view style="width: 100%;float: left;margin-top: 10px;width: 96%;margin-left: 2%;">
			<button type="primary"
				style="font-size: 10px;width: 100%;background-color: #1CBBB4;height: 40px;font-size: 14px;">支持作者
				多多分享</button>
		</view>
		<view style="width: 100%;float: left;margin-top: 10px;width: 96%;margin-left: 2%;">
			<button type="primary"
				style="font-size: 10px;width: 100%;background-color: #16A7F8;height: 40px;font-size: 14px;"  @click="back" >返回首页继续解析</button>
		</view>


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
		onLoad: function(option) {
			this.url = option.url
			//console.log(option.url);
			uni.request({
				url: 'https://newsaas.guangzhouzhuangxiu01.cn/api/xcx/index/getdouyinview', //仅为示例，并非真实接口地址。
				data: {
					url: this.url,

				},
				success: (res) => {
					//console.log(res.data);
					this.url = res.data;

				}
			});


		},
		methods: {
			click() {
				//console.log("123");
				uni.showLoading({
					title: '下载中'
				});
				uni.downloadFile({
					url: this.url, //仅为示例，并非真实的资源
					success: (res) => {
						var filePath=res.tempFilePath;
						if (res.statusCode === 200) {
							console.log('下载成功');
							
							uni.saveVideoToPhotosAlbum({
															filePath: res.tempFilePath,
															success: function() {
																uni.hideLoading()
																uni.showToast({
																	title: "保存成功",
																	icon: "none"
																});
															},
															fail: function() {
																uni.showModal({
																						content:'检测到您没打开获取信息功能权限，是否去设置打开？',
																						confirmText: "确认",
																						cancelText:'取消',
																						success: (res) => {
																							if(res.confirm){
																								uni.openSetting({
																									success: (res) => {
																										console.log(res);
																										uni.showToast({
																											title: "请重新点击分享保存图片～",
																											icon: "none"
																										});
																									}
																								})
																							}else{
																								uni.showToast({
																									title: "保存失败，请打开权限功能重试",
																									icon: "none"
																								});
																							}
																						}
																					})
																
															}
														});
						
							// uni.saveFile({
							//       tempFilePath: filePath,
							//       success: function (res) {
							//         console.log(res.savedFilePath);
							//       }
							// });
						}
					        uni.hideLoading();
					}
				});


			},
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
