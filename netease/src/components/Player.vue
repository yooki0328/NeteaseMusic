<template>
	<footer>
		<div id="btnGroup">
			<button></button>
			<button></button>
			<button></button>
		</div>
		<div id="time">
			<span>{{start|timeFormat}}</span>	
			<div id="processBar">
				
			</div>
			<span>{{end|timeFormat}}</span>	
			
		</div>
		<div id="volume">
			
		</div>
		<div id="other">
			<button></button>
			<button></button>
			<button></button>
		</div>
	</footer>
</template>
<style scoped>
	footer{
		background-color: #232326;
		width: 1000px;
		height: 70px;
		display: flex;
		align-items: center;
		justify-content: space-around;
	}
	footer #btnGroup{
		height: 40px;
		border: red 1px solid;
		margin-left: 20px;
	}
	footer #btnGroup button{
		width: 40px;
		height:40px;
	}
	footer #time{
		width: 300px;
		height: 40px;
		border: red solid 1px;
		display: flex;
	}
	footer #time #processBar{
		flex:1;
	}
	footer #volume{
		width: 150px;
		height: 40px;
		border: red solid 1px;
	}
	footer #other{
		width: 150px;
		height: 40px;
		border: red solid 1px;

	}
</style>
<script>
export default{
	name:'player',
	data(){
		return{
			start:'00:00',
			end:'00:00'
		}
	},
	methods:{
		createPlayer(){
			var audio = 
		}
	}
}
</script>