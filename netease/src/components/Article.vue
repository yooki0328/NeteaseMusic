<template>
    <article>
        <nav>
            <ul>
                <li v-for="(bar,index) in bars">
                    <a :href="bar.href" @click="changeBar(index)" :class="{actived:bar.isActive}">{{bar.title}}</a>
                </li>
            </ul>
        </nav>
		<div class="musicList List" v-show="barShow[0]">
        <dl>
			<dt>推荐歌单</dt>

			<dd v-for="list in lists">
				<div>
					<img :src="list.src" alt="pic">
					<a :href="list.href" class="list_text">{{list.text}}</a>
				</div>
			</dd>
        </dl>
		</div>
		<div class="radioFm" v-show="barShow[1]">
			
		</div>
		<div class="rankList" v-show="barShow[2]">
			
		</div>
		<div class="singers List" v-show="barShow[3]">
				<dl>
					<dt>热门歌手</dt>
					<dd v-for="singer in singers">
						<div>
							<img :src="singer.src" alt="pic">
							<a :href="singer.href" class="list_text">{{singer.text}}</a>
						</div>
					</dd>
				</dl>
		</div>
		<div class="musicNew" v-show="barShow[4]">
			
		</div>
    </article>
</template>
<script>
export default {
    name: 'article',
    data() {
        return {
            bars: [{
                title: '个性推荐',
                href: "#",
                isActive: true
            }, {
                title: '主播电台',
                href: "#",
                isActive: false
            }, {
                title: '排行榜',
                href: "#",
                isActive: false
            }, {
                title: '歌手',
                href: "#",
                isActive: false
            }, {
                title: '最新音乐',
                href: "#",
                isActive: false
            }, ],
            lists:[
           /* {src:"/static/pic.png",text:"好听的歌单",href:'#'},
            {src:"/static/pic.png",text:"好听的歌单",href:'#'},
            {src:"/static/pic.png",text:"好听的歌单",href:'#'},
            {src:"/static/pic.png",text:"好听的歌单",href:'#'},
            {src:"/static/pic.png",text:"好听的歌单",href:'#'},
            {src:"/static/pic.png",text:"好听的歌单",href:'#'},
            {src:"/static/pic.png",text:"好听的歌单",href:'#'},
            {src:"/static/pic.png",text:"好听的歌单",href:'#'}*/
            ],
			singers: [],
			barShow: [true,false,false,false,false]
        }
    },
    methods: {
        changeBar(index) {
			this.bars.forEach((val,ind)=>{
				val.isActive = false;
				this.barShow[ind] = false;
                if (ind === index) {
                    val.isActive = true;
					this.barShow[ind]=true;
                }
			})
        },
		getMusicList(){
			const url = "http://localhost:3000/personalized";

			this.$http.get(url).then(res=>{	
				var musicList = res.data.result;
				musicList.forEach(val=>{
					this.lists.push({
						src: val.picUrl,
						text: val.name,
						href: '#'
					});
				})
			})
		},
		getSingerList(){
			const url = "http://localhost:3000/top/artists";
			this.$http.get(url).then(res=>{
				var artists = res.data.artists
				console.log(artists)
				artists.forEach((val)=>{
					this.singers.push({
						src: val.img1v1Url,
						text: val.name,
						href: '#'
					})
				})
			})
		}
    },
	created(){
			this.getMusicList();
			this.getSingerList();
	}
}
</script>
<style scoped>
article {
	width: 800px;
	height: 500px;
    padding-left: 200px;
	padding-top:20px;
	background-color: #16181C;

}
article nav{
	margin-left:50px;
	padding-left:100px;
	border-bottom: #77787A 1px solid;
}
article ul{
	height:34px;
}
article ul li{
	list-style: none;
	float:left;
}
article ul li a{
	text-decoration: none;
	display: block;
	color: #77787A;
	padding:5px 10px;
	text-align:center;
}
article ul li a:hover{
	color: #CACBD1;
}
.actived {
    border-bottom: #CACBD1 solid 2px;
	color:#CACBD1;
}
article .List{
	width: 100%;
	height: 450px;
	overflow-x: hidden; 
	overflow-y: scroll;
}
article .List::-webkit-scrollbar{
	width: 4px;
	height: 100%;
}
article .List::-webkit-scrollbar-track{
	background-color: black;
}
article .List::-webkit-scrollbar-thumb{
	background-color: #7c2929;
}
article .List::-webkit-scrollbar-button{
	background-color: black;
}
article .List::-webkit-scrollbar-corner{
	background-color: black;
}
article dl{
	padding:20px 50px;
}
article dl dt{
	color:#A9AAB1;
	border-bottom: #77787A 1px solid;
}
article dl dd{
	float:left;
	width: 150px;
	height: 150px;
	margin-top: 20px;
	margin-bottom: 15px;
	margin-right: 15px;
}
article dl dd img{
	display: block;
	width: 150px;
	height: 150px;
}
article dl dd a{
	color: white;
	text-decoration: none;
	white-space: nowrap;
	font-size: 12px;
	text-overflow: ellipsis;
	overflow: hidden;
}
.list_text{
	padding-top:5px;
	display:block;
	text-align:center;
}
</style>
