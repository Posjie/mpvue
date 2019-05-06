<template>
	<div>
		我是用户页面
		<br>
		{{log}}
		<button @click="onClick()">执行方法</button>
		<ul v-for="(item,key) in list" :key="key">
			<li>{{item}}</li>
		</ul>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				log:'我是用户页面',
				list:[]
			}
			
		},
		methods:{
			onClick(){
				console.log('执行方法');
			}
		},
		created() {
			for(var i=0;i<=10;i++){
				this.list.push('这是第'+i+'个')
			}
		}
	}
</script>
  
<style>
</style>
