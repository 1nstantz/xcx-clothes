<template>
	<view class="home">
		<u-search placeholder="关键字" v-model="keyword" :showAction="false" @custom='searchClick'
			@search='searchClick'></u-search>

		<view class="ComBox">
			<div class="ComList" v-for="item in clothesList" :key="item.id">
				<div class="ImgBOX">
					<img :src="item.url" class="Img" alt="">
				</div>
				<div class="Title">
					{{item.label}}
				</div>
			</div>
		</view>

		<uni-fab ref="fab" :horizontal="horizontal" :vertical="vertical"
			 @fabClick="insert" />
	</view>

</template>

<script>
	export default {
		data() {
			return {
				keyword: '',
				clothesList: [
					"static/images/category.png",
					"static/images/category.png",
					"static/images/category.png"
				],
				vertical: 'bottom',
				horizontal: 'right',
			}
		},
		onLoad() {

		},
		methods: {
			searchClick() {

			},
			insert(){
				alert("点击添加")
			}
		}
	}
</script>

<style lang="scss" scoped>
	.ComBox {
		width: 690rpx; //根据微信定义设置  如非必要不建议改为100%；
		padding: 10rpx 30rpx;
		background-color: #f7f7f7;
		display: flex;
		justify-content: space-between;
		flex-wrap: wrap;

		.ComList {
			//未设置高度
			width: 270rpx;
			padding: 30rpx;
			background: #fff;
			border-radius: 8rpx;
			margin-top: 30rpx;

			.ImgBOX {
				width: 270rpx;
				height: 270rpx;
				border-radius: 12rpx;

				.Img {
					width: 100%;
					height: 100%;
				}
			}

			.label {
				width: 270rpx;
				font-size: 32rpx;
				line-height: 44rpx;
				height: 88rpx;
				padding-top: 15rpx;
				text-overflow: -o-ellipsis-lastline;
				overflow: hidden;
				text-overflow: ellipsis;
				display: -webkit-box;
				-webkit-line-clamp: 2;
				line-clamp: 2;
				-webkit-box-orient: vertical;
			}
		}
	}
</style>