<template>
	<footer>
		<audio :src="curMusic.src" ref="player" > </audio>
		<div id="btnGroup">
			<a href="javascript:;" class="playbar prev" @click=playPrev(curMusic.index)></a>
			<a href="javascript:;" :class="[playState,{playbar: true}]" @click = playMusicControll() ></a>
			<a href="javascript:;" class="playbar next" @click=playNext(curMusic.index)></a>
		</div>
		
		<div id="play-info">
			<div class="music-pic">
				<img :src="curMusic.img" alt="music-img" />
			</div>
			<div class="music-info">
				<div class="j-flag">
					<a href="javascript:;" class="curmusic-name">{{curMusic.name}}</a>
					<a href="javascript:;" class="curmusic-artist">{{curMusic.artist}}</a>
				</div>
				<div id="time">
						
					<input  id="processBar" type="range" @input=changeRangeBar($event) :style="audioColorBar" name="audio">
					<span id="timeStart">{{curTimec}}/</span>
					<span id="timeEnd">{{allTimec}}</span>	
				</div>
			</div>
			
		</div>
    <div id="music-list" v-show="musicListshow" class="listscroll">
      <h4 class="listhdc">播放列表</h4>
      <ul>
        <li v-for="(music,index) in musicList" :key="index">{{music.name}}</li>
      </ul>
    </div>
    <div id="music-list-button">
      <button @click="displayMusicList">播放列表</button>
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
footer {
  background-color: #373535;
  position: relative;
  width: 1000px;
  height: 70px;
  display: flex;
  align-items: center;
  /* justify-content: space-around; */
}
footer #btnGroup {
  height: 40px;
  margin-left: 20px;
  flex:1;
}
footer #btnGroup a {
  display: block;
  float: left;
  width: 28px;
  height: 28px;
  margin-right: 15px;
  margin-top: 5px;
  text-indent: -9999px;
}
footer #btnGroup .playbar {
  background-image: url("../assets/playbar.png");
}
footer #time {
  width: 80%;
  height: 30px;
  display: flex;
  align-items: center;
}
footer #time #processBar {
  height: 10px;
  display: flex;
  align-items: center;
  cursor: pointer;
  flex: 4;
  margin-right: 10px;
}
footer #time #processRed {
  width: 50%;
  height: 8px;
  background-color: red;
}
footer #time #timeStart,
footer #time #timeEnd {
  color: white;
  font-size: 15px;
}
footer #volume {
  width: 100px;
  height: 40px;
  display: flex;
  align-items: center;
  flex: 1;
}
footer #volume .volumeIcon {
  display: block;
  width: 25px;
  height: 25px;
  background-image: url("../assets/playbar.png");
  background-position: -2px -248px;
}
footer #volume #volumeControl {
  flex: 1;
  height: 10px;
  margin-left: 5px;
}
footer #volume .volumeControlOuter .volumeControlInner {
  width: 60%;
  height: 100%;
  background-color: pink;
  cursor: pointer;
}
footer #btnGroup .play {
  background-position: 0 -204px;
  width: 36px;
  height: 36px;
  margin-top: 0px;
}
footer #btnGroup .play:hover {
  background-position: -40px -204px;
}
footer #btnGroup .pause {
  background-position: 0 -165px;
  width: 36px;
  height: 36px;
  margin-top: 0px;
}
footer .prev {
  background-position: 0 -130px;
}
footer .prev:hover {
  background-position: -30px -130px;
}
footer .next {
  background-position: -80px -130px;
}
footer .next:hover {
  background-position: -110px -130px;
}
footer input[type="range"] {
  -webkit-appearance: none;
  width: 100%;
  border-radius: 10px;
}
footer input[type="range"]::-webkit-slider-thumb {
  -webkit-appearance: none;
}
footer input[type="range"]::-webkit-slider-runnable-track {
  box-shadow: 0 1px 1px #def3f8;
}
footer input[type="range"]:focus {
  outline: none;
}
footer input[type="range"]::-webkit-slider-thumb {
  -webkit-appearance: none;
  height: 100%;
  width: 5px;
  background-color: red;
  border-radius: 50%;
}
footer .j-flag a{
	text-decoration:none;
	outline: none;
	font-size: 14px;
}
footer .j-flag a:first-child{
	color: #e8e8e8;
}
footer .j-flag a:last-child{
	padding-left: 20px;
	color: #9b9b9b;
}
footer #play-info{
	display: flex;
  flex:2;
	align-items: center;
}
footer #play-info .music-pic{
	/* flex: 1; */
	margin-right: 20px;
}
footer #play-info .music-pic img{
  width: 34px;
  height: 34px;
}
footer #play-info .music-info{
  flex: 2;
}
footer #music-list{
  position: absolute;
  width: 300px;
  height: 300px;
  overflow-y: scroll;
  background-color:#191B1F;
  opacity:0.9;
  top: -300px;
  right: 20px;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
}
footer #music-list-button{
  /* flex:1; */
}
footer #music-list .listhdc{
  font-size: 16px;
  color: #e2e2e2;
  margin-bottom: 5px;
  padding-left: 15px;  
  background-color: black; 
}
footer #music-list ul{
  list-style-type: none;
}
footer #music-list ul li{
  padding-left: 30px;
  padding-top: 5px;
  padding-bottom: 5px;
  text-align: left;
  color: #ccc;
  border-bottom: #373535 1px solid;
}
footer .listscroll::-webkit-scrollbar{
	width: 4px;
	height: 100%;
}
footer .listscroll::-webkit-scrollbar-track{
	background-color: black;
}
footer .listscroll::-webkit-scrollbar-thumb{
	background-color: white;
}
footer .listscroll::-webkit-scrollbar-button{
	background-color: black;
}
footer .listscroll::-webkit-scrollbar-corner{
	background-color: black;
}
</style>
<script>
export default {
  name: "player",
  data() {
    return {
      curTime: "00:00",
      allTime: "00:00",
      playState: "play",
      volumeColorBar: "",
      audioColorBar: "",
      musicList: [
        // { 
        //   src: "../../static/music/岑宁儿 - 追光者.mp3",
        //   img: '../../static/img/jeay.jpg',
        //   name: '追光者',
        //   artist: '岑宁儿' 
        // },
        // { 
        //   src: "../../static/music/校长 - 带你去旅行.mp3",
        //   img: '../../static/img/jeay.jpg',
        //   name: '带你去旅行',
        //   artist: '校长'
        // },
        // { 
        //   src: "../../static/music/王建房 - 在人间.mp3",
        //   img: '../../static/img/jeay.jpg',
        //   name: '在人间',
        //   artist: '王建房'
        // },
        // { 
        //   src: "../../static/music/蔡健雅 - 红色高跟鞋.mp3",
        //   img: '../../static/img/jeay.jpg',
        //   name: '红色高跟鞋',
        //   artist: '蔡健雅'
        // },
        // { 
        //   src: "../../static/music/陈一发儿 - 童话镇.mp3",
        //   img: '../../static/img/jeay.jpg',
        //   name: '童话镇',
        //   artist: '陈一发儿' 
          
        // }
      ],
      musicListshow: false,
      curMusic: {
        index: 0,
        src: "../../static/music/校长 - 带你去旅行.mp3",
        img: '../../static/img/jeay.jpg',
        name: '带你去旅行',
        artist: '校长'
	    },
      // curMusic: {
      //     index: 0,
      // },
      timer: '',
    };
  },
  methods: {
    playMusicControll() {
      if (this.player.paused) {
        this.player.play();
        this.playState = "pause";
        this.curTime = this.player.currentTime;
        this.allTime = this.player.duration;
		setInterval(()=>{
      console.log(1)
			this.curTime = this.player.currentTime;
		},1000);
      } else {
        this.player.pause();
        this.playState = "play";
      }
    },
	switchMusic(index){
    this.curMusic = JSON.parse(JSON.stringify(this.musicList[index]));
    //this.getMusicDetail(this.curMusic.id)
      const url = "http://localhost:3000/music/url?id=" + this.curMusic.id;
      //console.log(url)      
      this.$http.get(url).then(res=>{
        //console.log(res.data.data);
        // console.log(res.data.data[0].url);
        this.curMusic.src = res.data.data[0].url;
        this.curMusic.index = index;
        // console.log(this.player)
        if(res.data.data[0].url){
          this.$nextTick(() => {
            this.player.play();
            this.playState = "pause";
            this.curTime = this.player.currentTime;
            this.player.oncanplay = ()=>{
              this.allTime = this.player.duration;
            }
      		});      
        }else{
            this.playState = "play";          
        }
      // this.allTime = this.player.duration;
        //this.curMusic.src = res.data.data[0].url;
        
      })
		
	},
    playNext(index) {
      let nextIndex = index + 1;
      let allIndex = this.musicList.length;
      if (nextIndex >= allIndex) {
        nextIndex = nextIndex % allIndex;
      }
      this.switchMusic(nextIndex);
    },
    playPrev(index) {
      let prevIndex = index - 1;
      let allIndex = this.musicList.length;
      if (prevIndex < 0) {
        prevIndex = prevIndex + allIndex;
      }
      this.switchMusic(prevIndex);
    },
    changeRangeBar(event) {
      var value = event.target.value;
      if (event.target.name == "audio") {

        this.curTime = this.player.currentTime = this.player.duration * (value/100);
        this.audioColorBar = `background: linear-gradient(90deg,red,red ${value}%,white ${value}%,white)`;
      } else {
        this.volumeColorBar = `background: linear-gradient(90deg,red,red ${value}%,white ${value}%,white)`;
      }
    },
    timeFormat(time) {
      
      let timeInt = parseInt(time),
          timeFormatt = '',
          timeSecond = parseInt(timeInt % 60),
          timeMinute = parseInt(timeInt / 60);
      timeSecond = timeSecond > 10 ? timeSecond : '0' + timeSecond;
      timeMinute = timeMinute > 10 ? timeMinute : '0' + timeMinute;
      timeFormatt = timeMinute + ':' + timeSecond;
      return timeFormatt;
    },
    getMusicList() {
      const url = "http://localhost:3000/top/list?idx=1";
				this.$http.get(url).then(res=>{
					let tracks = res.data.playlist.tracks.slice(0);
          //console.log(tracks)
          tracks.forEach((item,index)=>{
            let music = item.al;
            let singer = item.ar[0]; 
            
            this.musicList.push({
              src: '',
              id: music.id,
              img: music.picUrl,
              name: music.name,
              artist: singer.name
            });
          });
          //console.log(this.musicList);
				})
    },
    displayMusicList(){
      console.log(this.musicList)
      this.musicListshow = !this.musicListshow;
    }
    // getMusicDetail(id) {
    //   const url = "http://localhost:3000/music/url?id=" + id;
    //   //console.log(url)      
    //   this.$http.get(url).then(res=>{
    //     console.log(res.data.data);
    //     console.log(res.data.data[0].url);
        
    //     //this.curMusic.src = res.data.data[0].url;
        
    //   })
    // }
  },
  mounted() {
  this.player = this.$refs.player;
  this.getMusicList()
  },
  computed: {
	  curTimec: function(){
		  return this.timeFormat(this.curTime);
	  },
	  allTimec: function(){
		  return this.timeFormat(this.allTime);
	  },
  },
  watch: {
	  curTime: function(currentTime){
		  let value = (currentTime / this.allTime * 100).toFixed(2);
		  this.audioColorBar = `background: linear-gradient(90deg,red,red ${value}%,white ${value}%,white)`;
      if(value == 100){
        this.switchMusic(this.curMusic.index + 1);
      }
    }
  }
};
</script>
