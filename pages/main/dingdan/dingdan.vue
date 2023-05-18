<template>
	<view style="margin: 10upx;">
		<uni-section title-font-size="16px" title-color="#006776" title="订单管理" type="line"></uni-section>
		<view class="headstyle1">
			<view class="headstyle2" style="width: 250upx;">
				<uni-segmented-control :current="current" :values="items" style-type="button"
					:active-color="activeColor" @clickItem="onClickItem" />
			</view>
			<view v-if="current==1" class="headstyle3">
					选择时间段：
				<view width="280upx">
					<uni-datetime-picker v-model="range" type="daterange" @maskClick="maskClick" />
				</view>
			</view>
		</view>
		<view class="bodystyle1">
			<uni-table ref="table" :loading="loading" border stripe type="selection" emptyText="暂无更多数据"
				@selection-change="selectionChange">
				<uni-tr>
					<uni-th width="150" align="center">订单编号</uni-th>
					<uni-th width="80" align="center">类别</uni-th>
					<uni-th width="80" align="center">顾客姓名</uni-th>
					<uni-th width="80" align="center">顾客姓名</uni-th>
					<uni-th width="80" align="center">顾客姓名</uni-th>
					<uni-th width="80" align="center">顾客姓名</uni-th>
					<uni-th width="80" align="center">顾客姓名</uni-th>
					<uni-th width="80" align="center">顾客姓名</uni-th>
					<uni-th width="80" align="center">顾客姓名</uni-th>
					<uni-th width="80" align="center">顾客姓名</uni-th>
					<uni-th width="80" align="center">顾客姓名</uni-th>
					<uni-th width="80" align="center">设置</uni-th>
				</uni-tr>
				<uni-tr v-for="(item, index) in tableData" :key="index">
					<uni-td>{{ item.date }}</uni-td>
					<uni-td>
						<view class="name">{{ item.name }}</view>
					</uni-td>
					<uni-td align="center">{{ item.address }}</uni-td>
					<uni-td>
						<view class="uni-group">
							<button class="uni-button" size="mini" type="primary">修改</button>
							<button class="uni-button" size="mini" type="warn">删除</button>
						</view>
					</uni-td>
				</uni-tr>
			</uni-table>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				range: [Date.now(), Date.now()],
				current: 0,
				activeColor: '#006776',
				items: ['未完成订单', '已完成订单'],
			};
		},
		mounted() {
			uni.showToast({
				icon: 'loading',
				title: '请稍后……',
				duration: 500
			})
			console.log('已跳转到订单页面')
		},
		methods: {
			onClickItem(e) {
				if (this.current != e.currentIndex) {
					this.current = e.currentIndex;
				}
			},
			maskClick() {

			},
		}
	}
</script>

<style lang="scss">
	.headstyle3 {
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: flex-end;
		margin-right: 10upx;
		line-height: 35upx;
	}

	.headstyle2 {
		margin-left: 10upx;
	}

	.headstyle1 {
		display: flex;
		flex-direction: row;
	}

	.bodystyle1 {
		margin: 10upx;
	}
</style>
