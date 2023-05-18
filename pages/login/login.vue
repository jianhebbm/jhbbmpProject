<template>
	<view id="building" class="content_all">
		<view class="headstyle1">
			<image src="/static/jhbbm.png" mode="widthFix"></image>
		</view>
		<view class="headstyle2">
			客服电话:400-6677358
		</view>
		<view class="content_1 content">
			<view style="margin-top: 20upx;font-size: 25px;color: #fff;">健合帮帮盲门店管理系统</view>
			<view class="list">
				<view class="list-call">
					<image class="img" src="/static/shilu-login/phone.png"></image>
					<input class="biaoti" v-model="phoneno" type="number" maxlength="12" placeholder="输入手机号" />
				</view>
				<view class="list-call" style="margin-top: 20upx;">
					<image class="img" src="/static/shilu-login/block.png"></image>
					<input class="biaoti" v-model="password" type="text" maxlength="6" placeholder="六位数密码"
						password="true" />
				</view>
			</view>

			<!-- <view class="dlbutton" hover-class="dlbutton-hover" @tap="bindLogin()">
				<text>登录</text>
			</view> -->
			<view class="btnstyle">
				<button style="width: 60%;" type="primary" @click="bindLogin">登录</button>
			</view>
			<view class="otherlogin">
				二维码登录
			</view>
		</view>
		<view class="headstyle3">
			帮帮盲服务平台 All Rights Reserved
		</view>
	</view>
</template>

<script>
	export default {
		// 		onShow() {
		// 			var that = this
		// 			uni.request({
		// 				url: 'https://hn216.api.yesapi.cn/',
		// 				method: "POST",
		// 				header: {

		// 				},
		// 				data: {
		// 					model_name: 'Meun_person',
		// 					where: '[["id", ">","0"]]',
		// 					app_key: '0B4163C86181759DD5DE6C761AF719A5',
		// 					service: 'App.Table.FreeQuery',
		// 					perpage: 1000, //每一页12个数据
		// 				},
		// 				success: function(res) {
		// 					// console.log(res.data.data.list)
		// 					console.log(res)
		// 					that.people = res.data.data.list
		// console.log('数据为：'+that.people)
		// 				}
		// 			})
		// 		},
		data() {
			return {
				phoneno: '',
				password: '',
			};
		},
		methods: {
			bindLogin() {
				let that = this;
				uni.showLoading({
					title: "登录中…",
				});
				uni.request({
					url: getApp().globalData.apihost + "/service/login",
					data: {
						username: that.phoneno,
						password: that.password
					},
					success(res) {
						uni.hideLoading();
						if (res.data.resultid == '1') {
							getApp().globalData.accountUserInfo = res.data.data;
							uni.redirectTo({
								url: '/pages/main/main'
							})
						} else {
							uni.showToast({
								icon: 'error',
								title: "登陆失败：" + res.data.resultmsg,
								duration: 3000
							})
						}
					},
					fail(ret) {
						uni.hideLoading();
						console.log(ret);
						uni.showToast({
							icon: 'error',
							title: "登陆失败：" + ret.errMsg,
							duration: 3000
						})
					}
				})
			},








		}
	}
</script>

<style>
	.otherlogin{
		visibility: hidden;
		margin-top: 40upx;
		color: #FFFFFF;
		margin-left: 240upx;
	}
	#building {
		background: url("../../static/bg1.jpg");
		width: 100%;
		height: 100%;
		position: fixed;
		background-size: 100% 100%;
	}

	.content_all {
		display: flex;
		justify-content: flex-end;
		/* flex-direction: row; */
		align-items: center;
		height: 100vh;
		width: 100%;

	}

	.content_1 {
		width: 40%;
		height: 50%;
		margin-left: 100upx;

	}

	.content {
		display: flex;
		flex-direction: column;
		/* justify-content:flex-end; */
		/* align-items: center; */


	}

	.header {
		font-size: 50px;
	}


	.list {
		display: flex;
		flex-direction: column;
		padding-top: 40upx;
		/* padding-left: 70upx;
		padding-right: 70upx; */
	}

	.list-call {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		height: 20upx;
		color: #333333;
		width: 300upx;
		margin-bottom: 3upx;

		padding: 10upx;
		background-color: #F6F4FC;

	}

	.list-call .img {
		width: 20upx;
		height: 20upx;
	}

	.list-call .biaoti {
		flex: 1;
		text-align: left;
		font-size: 12upx;
		/* line-height: 100upx; */
		margin-left: 16upx;
	}

	.dlbutton {
		color: #FFFFFF;
		font-size: 12upx;
		width: 200upx;
		height: 55upx;
		background-color: #1890FF;

		align-items: center;
		display: flex;
		justify-content: center;

		line-height: 100upx;
		text-align: center;
		/* margin-left: auto;
		margin-right: auto; */
		margin-top: 30upx;
		/* margin-left: 30upx; */
	}

	.dlbutton hover {
		background-color: #1890cc;
	}

	.btnstyle {
		margin-top: 30upx;
		align-items: center;
		display: flex;
		justify-content: center;
		width: 300upx;
		/* background-color: red; */
	}

	.xieyi {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		font-size: 22upx;
		margin-top: 80upx;
		color: #FFA800;
		text-align: center;
		height: 40upx;
		line-height: 40upx;
	}

	.xieyi text {
		font-size: 22upx;
		margin-left: 15upx;
		margin-right: 15upx;
	}

	.headstyle1 {
		position: fixed;
		top: 20upx;
		left: 20upx;
	}

	.headstyle2 {
		color: #FFFFFF;
		position: fixed;
		top: 0;
		left: 1;
		margin-top: 50upx;
		margin-right: 50upx;
	}

	.headstyle3 {
		color: #555555;
		position: fixed;
		top: 95%;
		left: 0;
		width: 100%;
		text-align: center;
		border-top: #333333 2px solid;
	}
</style>
