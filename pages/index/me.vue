<template>
	<scroll-view>
		
		<view style="width: 100%;border-bottom: 1px  solid #dcdcdc;">
		
			<input class="uni-input" focus placeholder="请输入剧名"
				style="height: 50px;border: 0px solid red;margin-left: 10px;width: 73%;float: left;" v-model="namev" />
			<button class="mini-btn" type="primary" size="mini" style="margin-top: 10px;" @click="select()">查询</button>
		
		</view>
		
		<!-- <view style="margin-left: 1%;padding: 1%; font-weight : bold;font-size: 10px;">经典分类</view> -->
		<view style="width: 100%;margin-top: 10px;text-align: center;color:aliceblue" @click="say">
		    
	        
			<view  v-for="(item, index) in title" :key = "index" >
				
				
				<view v-if="index%3==1" 
				style="width: 30%;margin-left: 1%;background:linear-gradient(90deg,#CB0E97 0%,#7533B2 100%); ;float: left;padding: 1%;height: 20%;margin-bottom: 10px;"><span style="font-size: 15px;">{{item}}</span></view>
				
				<view v-if="index%3==2"
				style="width: 30%;margin-left: 1%;background:linear-gradient(90deg,#048AF3 0%,#19B6BB 100%) ;float: left;padding: 1%;height: 20%;margin-bottom: 10px;"><span style="font-size: 15px;">{{item}}</span></view>
				
				
				<view v-if="index%3==0"
				style="width: 30%;margin-left: 1%;background:linear-gradient(90deg,#048AF3 0%,#19B6BB 100%); ;float: left;padding: 1%;height: 20%;margin-bottom: 10px;"><span style="font-size: 15px;">{{item}}</span></view>
				
			</view>
		
		
		
		</view>
		
		
		
		
		
		
		
		<view style="margin-left: 1%;padding:2%; font-weight : bold;font-size: 10px;margin-top: 120px;">热门推荐</view>
		
		<view style="width: 100%;margin-top: 0px;text-align: center;color:aliceblue" >
		    
			<view v-for="(item, index) in vedio" :key = "index" 
				style="width: 30%;margin-left: 1%; ;float: left;padding: 1%;height: 20%;">
				
				
					
				
				
				
				<view>
				   
				    <!-- <a :href="'https://newsaas.guangzhouzhuangxiu01.cn/api/xcx/index/vedio?url='+item.vediourl"> -->
					 <image @click="redirectUrl(item.vediourl)" style="width: 90%;height: 130px;border-radius: 5px;position: relative;" :src="item.img" mode="aspectFill"></image>
					<!-- </a> -->
					
					
					<span id="fenshu" class="fed-list-score fed-font-xii fed-back-green" z-index=2 style="width: 25px;position:absolute;float: left;margin-left: -26%;margin-top: 5px;">
					{{item.fenshu}}
					</span>
					<view class="image-title" style="text-align: left;margin-left:4%;color:#666666;float:left;;font-size:10px;width:100%;overflow-x:hidden!important;overflow-y:hidden;overflow:hidden; text-overflow:ellipsis;white-space:nowrap;">{{item.name}}</view>
			
					<view style="color:#666666;float:left;font-size:10px;margin-left: 4%;width: 100%;">
						<UniRate readonly="true" size="12" :value="item.fenshu/2" color="#bbb" active-color="#FF5252"></UniRate>
					</view>
				</view>
				
			</view>
		
	
			
			
		
		</view>
	
		<!-- <view style="width: 100%;margin-top: 0px;text-align: center;color:aliceblue" @click="say">
		    
			<view
				style="width: 30%;margin-left: 1%; ;float: left;padding: 1%;height: 20%;">
				<view>
					<image style="width: 90%;height: 130px;border-radius: 5px;" src="http://pic8.iqiyipic.com/image/20220613/fc/e8/v_166862983_m_601_m1_260_360.jpg" mode="aspectFill"></image>
					<view class="image-title" style="color:#666666;float:left;font-size:10px;margin-left: 4%;">神秘海域</view>
				</view>
				
			</view>
		
			<view
				style="width: 30%;margin-left: 1%; ;float: left;padding: 1%;height: 20%;">
				<view>
					<image style="width: 90%;height: 130px;border-radius: 5px;" src="http://pic7.iqiyipic.com/image/20220610/38/ca/v_167769901_m_601_m2_260_360.jpg" mode="aspectFill"></image>
					<view class="image-title" style="color:#666666;float:left;font-size:10px;margin-left: 4%;">出拳吧 妈妈</view>
				</view>
				
			</view>
			
			<view
				style="width: 30%;margin-left: 1%; ;float: left;padding: 1%;height: 20%;">
				<view>
					<image style="width: 90%;height: 130px;border-radius: 5px;" src="http://pic5.iqiyipic.com/image/20220604/26/f3/v_167005096_m_601_m5_260_360.jpg" mode="aspectFill"></image>
					<view class="image-title" style="color:#666666;float:left;font-size:10px;margin-left: 4%;">盲战</view>
				</view>
				
			</view>
			
			
		
		</view>
		 -->
	</scroll-view>
	
	
	
</template>

<script>
	import UniRate from '@/uni_modules/uni-rate/uni-rate.vue';
	export default {
		components: {UniRate},
		data() {
			return {
				currentPage:1,
				currentSize:15,
				totalPage:60,
				title: ['动作','剧情','搞笑','网络','言情','武侠','偶像','青春','都市'],
				vedio:[
				{name:"海之谣",img:"https://pic1.iqiyipic.com/image/20220513/e4/ec/a_100505673_m_601_260_360.jpg",fenshu:"9.6",vediourl:""},
				{name:"乌龙山剿匪记",img:"http://pic2.iqiyipic.com/image/20220505/9e/f2/a_100009592_m_601_m3_260_360.jpg",fenshu:"8.4",vediourl:""},
				{name:"暗夜行者",img:"http://pic9.iqiyipic.com/image/20220606/ab/09/a_100459594_m_601_m6_260_360.jpg",fenshu:"8.8",vediourl:""},
				{name:"神秘海域",img:"http://pic8.iqiyipic.com/image/20220613/fc/e8/v_166862983_m_601_m1_260_360.jpg",fenshu:"7.5",vediourl:""},
				{name:"出拳吧 妈妈",img:"http://pic7.iqiyipic.com/image/20220610/38/ca/v_167769901_m_601_m2_260_360.jpg",fenshu:"9.6",vediourl:""},
				{name:"盲战",img:"http://pic5.iqiyipic.com/image/20220604/26/f3/v_167005096_m_601_m5_260_360.jpg",fenshu:"9.0",vediourl:""},
				],
				url: '',
				namev:''
			}
		},
		onLoad() {
			uni.request({
				url: 'https://newsaas.guangzhouzhuangxiu01.cn/api/xcx/index/getmzinfo', //仅为示例，并非真实接口地址。
				data: {
					flag: 'mz',
					
			
				},
				success: (res) => {
					if(res.data['vedio'] !==undefined && res.data['vedio'].length > 0){
						this.vedio=res.data['vedio'];
					}
					
					this.title=res.data['list'];
					this.totalPage=res.data['num']
					
			
				}
			});
			
		},
		onPullDownRefresh() {
		    console.log('refresh');
			
			uni.request({
				url: 'https://newsaas.guangzhouzhuangxiu01.cn/api/xcx/index/getmzinfo', //仅为示例，并非真实接口地址。
				data: {
					flag: 'mz',
					
			
				},
				success: (res) => {
					if(res.data['vedio'] !==undefined && res.data['vedio'].length > 0){
						this.vedio=res.data['vedio'];
					}
					
					this.title=res.data['list'];
					this.totalPage=res.data['num']
					uni.stopPullDownRefresh();
			
				}
			});
			
			
		        
		},
		onReachBottom() {
			this.currentPage++;
			if (this.currentPage > this.totalPage) {
				uni.hideNavigationBarLoading();
				uni.showToast({
							title: '暂无更多数据'
				})
			} else {
				this.getScrollList(this.currentPage, this.currentSize);
				//console.log(this.currentPage);
			}
		},
		computed:{
		},
		methods: {
			select(){
				console.log(this.namev);
				
				uni.showLoading({
					title: '查询中'
				});
				
				uni.request({
					url: 'https://newsaas.guangzhouzhuangxiu01.cn/api/xcx/index/getmzinfo', //仅为示例，并非真实接口地址。
					data: {
						flag: 'mz',
						name:this.namev
				
					},
					success: (res) => {
					
						this.vedio=res.data['vedio'];
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
			
			redirectUrl:function(id){
				console.log(id)
				// uni.setClipboardData({
				// 	data: 'https://newsaas.guangzhouzhuangxiu01.cn/api/xcx/index/vedio?url='+id,
				// 	success: function() {
				// 		// console.log(this)
				// 		uni.showToast({ //uni默认吐司
						
				// 		    title: '已复制链接  请手机浏览器打开观看', //提示内容
						
				// 		    duration: 500 //提示显示时间
						
				// 		});
				// 	}
				// })
				
				
				uni.navigateTo({
					url: 'vedio?url=' +id,
					success(res) {
						 //console.log('成功啦',res);
						},
						fail(err) {
						//console.log('失败啦',err);
						}
						
				});
				// uni.redirectTo({
				//             url: 'https://newsaas.guangzhouzhuangxiu01.cn/api/xcx/index/vedio?url='+id
				// });
			},
					
			getScrollList(current, size) {
				
				uni.request({
					url: 'https://newsaas.guangzhouzhuangxiu01.cn/api/xcx/index/getmzinfo', //仅为示例，并非真实接口地址。
					data: {
						flag: 'mz',
						page:current,
						pagenum:size
				
					},
					success: (res) => {
						this.totalPage=res.data['num'];
						if(res.data['vedio'] !==undefined && res.data['vedio'].length > 0){
							this.vedio=this.vedio.concat(res.data['vedio']);
						}
						
						
						
				
					}
				});
				
			},
			say(){
				 uni.showToast({ //uni默认吐司
				
				    title: '联系作者', //提示内容
				
				    duration: 500 //提示显示时间
				
				});
				
			},
		}
	}
	
	
</script>

<style>

.fed-list-info .fed-list-score {
    position: absolute;
    top: .3125rem;
    left: -.3125rem;
    padding: 0 .3125rem;

}

.fed-head-info .fed-pops-navbar .fed-this a:before, .fed-swip-this, .fed-back-green {
    background-color: #0bbe06!important;
}

.fed-font-xii {
    font-size: .75rem!important;
}
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Helvetica,Arial,Microsoft Yahei,sans-serif;
    -webkit-tap-highlight-color: transparent;
}


#fenshu:before{
    
       content: "";
       border-top: .25rem solid #0bbe06;
	   position: absolute;
	   left: .0625rem;
	   bottom: -.25rem;
	   border-top: .25rem solid #0bbe06;
	   border-left: .25rem solid transparent;
}


	
	
</style>