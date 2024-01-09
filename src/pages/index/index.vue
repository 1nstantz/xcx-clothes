<template>
	<view class="home">
		<!-- 搜索条件 -->
		<el-select v-model="season"  placeholder="选择季节" style="width:20% ">
			<el-option
			v-for="item in seasons"
			:key="item.value"
			:label="item.label"
			:value="item.value">
			</el-option>
		</el-select>
		<!-- 搜索类别 -->
		<el-autocomplete
			class="inline-input"
			v-model="categoryId" 
			:fetch-suggestions="querySearch"
			placeholder="输入分类"
			@select="handleSelect"  style="width:30% "
		></el-autocomplete>
		<el-button type="primary" icon="el-icon-search">搜索</el-button>
		<!-- 图片 -->
		<view class="ComBox">
			<div class="ComList" v-for="item in clothesList" :key="item.id">
				<div class="ImgBOX">
					<img :src="item" class="Img" alt="">
				</div>
				<div class="Title">
					{{item.label}}
				</div>
			</div>
		</view>
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
					"static/images/category.png",
					"static/images/category.png",
					"static/images/category.png",
					"static/images/category.png",
					"static/images/category.png",
					"static/images/category.png",
					"static/images/category.png",
					"static/images/category.png"
				],
				vertical: 'bottom',
				horizontal: 'right',
				seasons: [{label: "春秋",value: 1},{label: "夏",value: 2},{label: "冬",value: 3}],
				season: '',
				categorys: [],
				categoryId:''
			}
		},
		onLoad() {
			
		},
		methods: {
			querySearch(queryString, cb) {
				var results  = this.categorys;
				this.results = queryString ? results.filter(this.createFilter(queryString)) : results;
				//调用 callback 返回建议列表的数据
				cb(results);
			},
			searchClick() {

			},
			createFilter(queryString) {
				return (item) => {
					return item.categoryName.toUpperCase().match(queryString.toUpperCase());
				};
			},
			loadCategorys() {
				return [{categoryName: "T恤",categoryId: 1},{categoryName: "外套",categoryId: 2},{categoryName: "连衣裙",categoryId: 3},{categoryName: "鞋子",categoryId: 4}]
			},
			handleSelect(item) {
				console.log(item);
			}
		},
		mounted() {
			this.categorys = this.loadCategorys();
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