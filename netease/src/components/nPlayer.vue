<template>
	<footer>
		<audio :src="curMusic.src" ref="player" > </audio>
		<div id="btnGroup">
			<a href="javascript:;" class="playbar prev"></a>
			<a href="javascript:;" :class="[playState,{playbar: true}]" @click = playMusicControll() ></a>
			<a href="javascript:;" class="playbar next" @click=playNext(curMusic.index)></a>
		</div>
		<div id="time">
			<span id="timeStart">{{start}}</span>	
		<!--	<div id="processBar">-->
				<!--<div id="processRed"></div>-->
				<input  id="processBar" type="range" @input=changeRangeBar($event) :style="audioColorBar" name="audio">
		<!--	</div>-->
			<span id="timeEnd">{{end}}</span>	
			
		</div>
		<div id="volume">
		<div>
		
			<a href="#" class="volumeIcon"></a>
		</div>
			<!--	<div class="volumeControlInner"></div>-->
			<input id="volumeControl" type="range" @input=changeRangeBar($event) :style="volumeColorBar" name="volume">
			
		</div>
	</footer>
</template>
<style scoped>
	footer{
		background-color: #373535;
		width: 1000px;
		height: 70px;
		display: flex;
		align-items: center;
		justify-content: space-around;
	}
	footer #btnGroup{
		height: 40px;
		margin-left: 20px;
	}
	footer #btnGroup a{
		display: block;
		float: left;
		width: 28px;
		height: 28px;
		margin-right: 15px;
		margin-top: 5px;
		text-indent: -9999px;
	}
	footer #btnGroup .playbar{
		background-image:url("../assets/playbar.png");
	}
	footer #time{
		width: 300px;
		height: 40px;
		display: flex;
		align-items: center;
	}
	footer #time #processBar{
		height: 10px;
		display: flex;
		align-items: center;
		cursor: pointer;
		flex: 4;
		margin-right: 10px;
	}
	footer #time #processRed{
		width: 50%;
		height:8px;
		background-color: red;
	}
	footer #time #timeStart, footer #time #timeEnd{
		color: white;
		font-size: 15px;
		flex: 1;
	}
	footer #volume{
		width: 100px;
		height: 40px;
		display: flex;
		align-items: center;
	}
	footer #volume .volumeIcon{
		display: block;
		width: 25px;
		height: 25px;
		background-image:url("../assets/playbar.png");
		background-position: -2px -248px;
	}
	footer #volume #volumeControl{
		flex: 1;
		height: 10px;
		margin-left: 5px;
	}
	footer #volume .volumeControlOuter .volumeControlInner{
		width: 60%;
		height: 100%;
		background-color: pink;
		cursor: pointer;
	}
	footer #btnGroup .play{
		background-position:0 -204px;
		width: 36px;
		height: 36px;
		margin-top: 0px;
	}
	footer #btnGroup .play:hover{
		background-position: -40px -204px;
	}
	footer #btnGroup .pause{
		background-position:0 -165px;
		width: 36px;
		height: 36px;
		margin-top: 0px;
	}
	footer .prev{
		background-position:0 -130px;
	}
	footer .prev:hover{
		background-position:-30px -130px;
	}
	footer .next{
		background-position:-80px -130px;
	}
	footer .next:hover{
		background-position: -110px -130px;
	}
	footer input[type=range]{
		-webkit-appearance: none;
		width: 100%;
		border-radius:10px;
	}
	footer input[type=range]::-webkit-slider-thumb{
		-webkit-appearance: none;
	}
	footer input[type=range]::-webkit-slider-runnable-track{
		box-shadow: 0 1px 1px #def3f8;
	}
	footer input[type=range]:focus{
		outline: none;
	}
	footer input[type=range]::-webkit-slider-thumb{
		-webkit-appearance: none;
		height: 100%;
		width: 5px;
		background-color: red;
		border-radius: 50%;
	}
</style>
<script>
export default{
	name:'player',
	data(){
		return{
			start:'00:00',
			end:'05:00',
			playState: 'play',
			volumeColorBar: "",
			audioColorBar: "",
			musicList: [
				{src: '../../static/music/岑宁儿 - 追光者.mp3'},
				{src: '../../static/music/校长 - 带你去旅行.mp3'},
				{src: '../../static/music/王建房 - 在人间.mp3'},
				{src: '../../static/music/蔡健雅 - 红色高跟鞋.mp3'},
				{src: '../../static/music/陈一发儿 - 童话镇.mp3'},
			],
			curMusic: {
				index: 1,
				src: '../../static/music/校长 - 带你去旅行.mp3'
			}
		}
	},
	methods:{
		playMusicControll(){
			
				if(this.player.paused){
					this.player.play();	
					this.playState = 'pause';
				}else{
					this.player.pause();
					this.playState = 'play';
				}
		},
		playNext(index){
			
			let nextIndex = index + 1;
			let allIndex = this.musicList.length;
			if( nextIndex >= allIndex) {
				nextIndex = nextIndex % allIndex;
			}
			this.curMusic.src = this.musicList[nextIndex].src;
			this.curMusic.index = nextIndex;
			this.player.play();
			this.$nextTick(()=>{
				this.player.play();
			})
			
		},
		changeRangeBar(event) {
			var value = event.target.value;
			if(event.target.name=="audio"){
				this.audioColorBar = `background: linear-gradient(90deg,red,red ${value}%,white ${value}%,white)`
			}else{
			
				this.volumeColorBar = `background: linear-gradient(90deg,red,red ${value}%,white ${value}%,white)`
			}
		},

	},
	mounted(){
		this.player = this.$refs.player;
	}
}
</script>
