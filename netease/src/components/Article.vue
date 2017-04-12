<template>
    <article>
        <nav>
            <ul>
                <li v-for="(bar,index) in bars">
                    <a :href="bar.href" @click="changeBar(index)" :class="{actived:bar.isActive}">{{bar.title}}</a>
                </li>
            </ul>
        </nav>
        <div style="width: 500px;height: 150px;">
        	
        </div>
        <dl>
			<dt>推荐歌单</dt>

			<dd v-for="list in lists">
				<div>
					<img :src="list.src" alt="pic">
					<a :href="list.href">{{list.text}}</a>
				</div>
			</dd>
        </dl>
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
                title: '歌单',
                href: "#",
                isActive: false
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
            {src:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1986147978,3326401307&fm=111&gp=0.jpg",text:"lalalala",href:'#'},
            {src:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1986147978,3326401307&fm=111&gp=0.jpg",text:"lalalala",href:'#'},
            {src:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1986147978,3326401307&fm=111&gp=0.jpg",text:"lalalala",href:'#'},
            {src:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1986147978,3326401307&fm=111&gp=0.jpg",text:"lalalala",href:'#'},
            {src:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1986147978,3326401307&fm=111&gp=0.jpg",text:"lalalala",href:'#'},
            {src:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1986147978,3326401307&fm=111&gp=0.jpg",text:"lalalala",href:'#'},
            {src:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1986147978,3326401307&fm=111&gp=0.jpg",text:"lalalala",href:'#'},
            {src:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1986147978,3326401307&fm=111&gp=0.jpg",text:"lalalala",href:'#'},
            {src:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1986147978,3326401307&fm=111&gp=0.jpg",text:"lalalala",href:'#'},
            {src:"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1986147978,3326401307&fm=111&gp=0.jpg",text:"lalalala",href:'#'}
            ]
        }
    },
    methods: {
        changeBar(index) {
            this.bars.forEach(function(val, ind) {
                val.isActive = false;
                if (ind === index) {
                    val.isActive = true;
                }
            })
        }
    }
}
</script>
<style scoped>
article {
	width: 1000px;
	height: 500px;
	box-sizing: border-box;
    padding-left: 200px;
	background-color: #16181C;

}
article nav{
	padding-left:100px;
	border-bottom: #77787A 1px solid;
}
article ul li{
	list-style: none;
	display: inline-block;
	margin-left:10px;
}
article ul li a{
	text-decoration: none;
	display: block;
	padding: 5px;
	color: #77787A;
}
article ul li a:hover{
	color: #CACBD1;
}
.actived {
    border-bottom: #CACBD1 solid 2px;
	color:#CACBD1;
}
article dl{
	margin:10px 110px;
	width: 600px;
	height:220px;
	overflow: hidden;	
}
article dl dt{
	color:#A9AAB1;
	border-bottom: #77787A 1px solid;
}
article dl dd{
	display: inline-block;
	width: 100px;
	height: 120px;
	border: red solid 1px;
	margin-top: 20px;
	margin-bottom: 15px;
	margin-right: 10px;
}
article dl dd img{
	display: block;
	width: 100px;
	height: 100px;
}
article dl dd a{
	color: white;
	text-decoration: none;
}

</style>
