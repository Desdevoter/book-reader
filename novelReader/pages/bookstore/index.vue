<template>
	<view class="content">
		<view class="status_bar">
		    <!-- 这里是状态栏 -->
		</view>
		<view class="store-list">
			<view class="store-item" v-for="item in storeAry" :key="item.id" @click="turnToRead(item)">
				<view class="logo">
					<image :src="item.img" mode=""></image>
				</view>
				
				<view class="content">
					<view class="title">
						{{ item.name }}
					</view>
					<view class="sup-title">
						{{ item.lastUpdate.title }}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				storeAry: [{
					id: 13959,
					name: '圣墟',
					img: 'http://www.xbiquge.la/files/article/image/13/13959/13959s.jpg',
					lastUpdate: {
						title: '第1568章 禁忌',
						url: 'http://www.xbiquge.la/13/13959/25965726.html'
					}
				}, {
					id: 15003,
					name: '道君',
					img: 'http://www.xbiquge.la/files/article/image/15/15003/15003s.jpg',
					lastUpdate: {
						title: '新书《前任无双》正式发布',
						url: 'http://www.xbiquge.la/15/15003/17962464.html'
					}
				}]
			}
		},
		onLoad() {
			uni.setStorage({
				key: 'storeMsg',
				data: this.storeAry,
				success: (res) => {
					console.log(res)
				}
			})
		},
		methods: {
			turnToRead(data) {
				uni.navigateTo({
					url: '/pages/read/index'
				})
			}
		}
	}
</script>

<style lang="less">
	.status_bar {
	      height: var(--status-bar-height);
	      width: 100%;
	  }
	  
	.store-list {
		padding: 10px;
		
		.store-item {
			display: flex;
			align-items: center;
			vertical-align: center;
			padding: 12px 10px;
			border-bottom: 1px solid #eee;
			
			.logo {
				width: 32px;
				padding-right: 16px;
				
				image {
					display: inline-block;
					width: 100%;
					height: 45px;
				}
			}
			
			.content {
				flex: 1;
				margin-top: -10px;
				
				.title {
					font-size: 14px;
					font-weight: 700;
					font-family: '微软雅黑';
					padding: 0;
					margin: 0;
				}
				
				.sup-title {
					color: #999;
					text-overflow: ellipsis;
					overflow: hidden;
					white-space: nowrap;
					font-size: 12px;
					margin-top: 6px;
				}
			}
		}
	}
</style>
