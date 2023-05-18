<template>
	<view class="mainstyle">
		<!-- 顶部 -->
		<view class="topstyle">
			<view class="headimgstyle0">
				<image src="../../static/jhbbm.png" mode="widthFix" class="headimgstyle"></image>
			</view>
			<view class="topTextStyle1">
				XXXX店
			</view>
			<view class="topTextStyle2">
				<view class="topTextStyle3">
					<view class="topTextStyle4">
						提醒
					</view>
					<view class="topTextStyle4">
						使用帮助
					</view>
					<view>
						[店长]张三
					</view>
				</view>
			</view>
		</view>
		<!-- 下部 -->
		<view class="rightstyle0">
			<!-- 左侧列表 -->
			<view class="leftstyle1">

				<view v-for="(item,index) in listdata" :key="index" class="leftbottom">
					<view :class="item.name==selectItemName?'leftitem1':'leftitem0'" @click="selectItem(item.name)">
						{{item.text}}
					</view>
				</view>
			</view>
			<!-- 右侧内容 -->
			<view class="rightbottom">
				<scroll-view class="rightstyle1" scroll-x="true" scroll-y="true">
					<component :is="selectItemName"></component>
				</scroll-view>

			</view>
		</view>
	</view>
</template>

<script>
	import yuDingForm from "./yuding/yuding.vue";
	import dingDanForm from "./dingdan/dingdan.vue";
	export default {
		components: {
			yuDingForm,
			dingDanForm
		},
		data() {
			return {
				selectItemName: 'yuDingForm',
				listdata: [{
						text: '预订管理',
						name: 'yuDingForm'
					},
					{
						text: '订单管理',
						name: 'dingDanForm'
					},
					{
						text: '会员管理',
						name: 'huiYuanForm'
					},

				],
			};
		},
		computed: {

		},
		methods: {
			selectItem(e) {
				this.selectItemName = e
			},



		},
	}
</script>

<style lang="scss">
	.leftitem2 {
		color: #ffffff;
		background-color: coral;
		height: 40upx;
		line-height: 40upx;
	}

	.leftitem1 {
		color: #ffffff;
		background-color: orangered;
		height: 40upx;
		line-height: 40upx;
	}

	.leftitem0 {
		color: #ffffff;
		height: 40upx;
		line-height: 40upx;
	}

	.leftbottom {
		width: 100%;
		text-align: center;
		// margin-left: 10upx;
		// margin-right: 10upx;
		margin-top: 30upx;
		// background-color: red;
		height: 30upx;
	}

	.headimgstyle0 {
		height: 60upx;
		// border-bottom: #ffffff 2upx solid;
	}

	.headimgstyle {
		width: 180upx;
		height: 50upx;
		padding: 10upx;
		margin-left: 20px;
	}

	.rightbottom {
		width: 100%;
		height: 100%;
	}

	.rightstyle1 {
		// margin: 15upx;
		// background-color: red;
		height: 100%;
		width: 100%;
	}

	.rightstyle0 {
		display: inline-flex;
		// background-color: green;
		height: 100%;
		width: 100%;
	}

	.leftstyle1 {
		display: flex;
		flex-direction: column;
		background-color: #006776;
		width: 130upx;
		min-width: 130upx;
		height: 100%;
	}

	.mainstyle {
		display: flex;
		flex-direction: column;
		height: 100vh;
		width: 100vw;
	}

	.biaoti {
		font-size: 14px;
		font-weight: bold;
	}

	.topTextStyle4 {
		margin-right: 30upx;
	}

	.topTextStyle3 {
		color: #006776;
		display: flex;
		justify-content: flex-end;
		width: 300upx;
		margin-right: 30upx;
		line-height: 90upx;
	}

	.topTextStyle2 {
		display: flex;
		width: 100%;
		justify-content: flex-end;
	}

	.topTextStyle1 {
		justify-content: flex-start;
		width: 100%;
		margin-left: 50upx;
		line-height: 90upx;
		// background-color: red;
		min-width: 200upx;
	}

	.topstyle {
		display: flex;
		height: 70upx;
		width: 100%;
		// background-color: green;
		border-bottom: #006776 2px solid;
	}

	.bottomstyle {
		height: 100%;
		width: 100%;
	}
</style>
