<template>
	<view class="pointer">
		<template v-for="(item,index) in data">
			
			<template v-if="!item.children || !item.children.length">
				<uni-menu-item :index="item">
					<view :class="item.icon"></view>
					<text :class="{title: item.icon}">{{item.text}}</text>
				</uni-menu-item>
			</template>
			<uni-sub-menu v-else :index="item" :isactive="index==isactivenum?true:false">
				<template v-slot:title>
					<view @click="get(item.children,index)" class="_icon" style="" :class="item.icon"></view>
					<text @click="get(item.children,index)" :class="{title: item.icon}">{{item.text}}</text>
				</template>
			</uni-sub-menu>
		</template>
	</view>
</template>

<script>
	import uniMenuSidebar from '../uni-menu-sidebar/uni-menu-sidebar.vue'
	export default {
		name: 'uniMenuSidebar',
		components: {
			uniMenuSidebar
		},
		props: {
			data: {
				type: Array,
				default () {
					return []
				}
			},
			isactivenum: {
				type: Number,
				default () {
					return 0
				}
			},
		},
		data() {
			return {
				
			};
		},
		computed: {

		},
		methods: {
			get(e,_index){
				this.$emit("getChild1",e,_index);
			}
		}
	}
</script>

<style lang="scss">
	
	.title {
		// margin-left: 5px;
		text-align: center;
		width: 100%;
		height: 30px;
		line-height: 30px;
		
	}
	._icon{
		width: 100%;
		text-align: center;
		height: 20px;
		color: #fff;
		line-height: 20px;
	}
	.uni-nav-menu.to .uni-sub-menu{
		position: relative;
		// transition: all .3s;
	}
	.uni-nav-menu.to .uni-sub-menu.active{
		border-left: 3px solid rgb(64, 158, 255);
		border-top: 3px solid rgb(64, 158, 255);
		border-right: 0px;
		border-bottom: 3px solid rgb(64, 158, 255);
		background: #fff;
		
		// border-radius: 5px;
	}
	.uni-nav-menu.to .uni-sub-menu::before{
		content:"";
		position: absolute;
		width: 3px;
		height: 101%;
		top: 0px;
		z-index: 2;
		right: -3px;
		background: rgb(64, 158, 255);
	}
	.uni-nav-menu.to .uni-sub-menu.active::before{
		content:"";
		position: absolute;
		width: 3px;
		height: 101%;
		top: 0px;
		z-index: 2;
		right: -3px;
		background: #fff;
	}
	.uni-nav-menu.to .uni-sub-menu.active .title{
		color: rgb(64, 158, 255);
	}
	.uni-nav-menu.to .uni-sub-menu.active ._icon{
		color: rgb(64, 158, 255);
	}
	.uni-nav-menu.to .uni-sub-menu .title, .uni-nav-menu.to .uni-sub-menu ._icon{
		color: #fff;
	}
</style>
