<template name="hello">  <!-- 定义组件的名称为hello -->
	<view>
		{{msg}}
		<view>
			<input type="text" :value="myval" class="txt"/>
		</view>
	</view>
</template>

<script>
	export default {
		// 定义组件的名称为hello
		name:"hello",
		
		data() {
			return {
				msg:"你好，这是自定义组件~"
			}
		},
		methods: {
			
		},
		// 接收父级组件传值
		props: {
			myval: {
				type: String
			}
		}
	}
</script>

<style>
.txt {
		color: green;  
	}
</style>
