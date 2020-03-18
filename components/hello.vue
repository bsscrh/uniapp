<template name="hello">  <!-- 定义组件的名称为hello -->
	<view>
		{{msg}}
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
			
		}
	}
</script>

<style>

</style>
