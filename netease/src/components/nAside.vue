<template>
  <aside>
    <nav>
      <ul>
        <li v-for="(list,index) in lists">
          <a :href="list.href" @click="changeBar(index)" :class="{actived:list.isActive}" >{{list.title}}</a>
        </li>
      </ul>
    </nav>
  </aside>
</template>
<style scoped>
  aside{
  padding:20px 0 0 0;
  float:left;
  width:200px;
  height:500px;
  background-color:#191B1F;
  overflow:hidden;
  }

 nav ul li{
  list-style:none;
 } 
 nav ul li a{
  display:block;
  width:100%;
  box-sizing:border-box;
  padding:10px 0;
  padding-left:50px;
  text-decoration:none;
  color:#ADAFB2;
 }
 nav ul li a:hover{
  color:#f1f1f1;
  background-color:#27282c;
 }
 .actived{
  background-color:#27282C;
  border-left:#B82525 solid 4px;
  color:white;
 }
</style>
<script>
  export default{
    name:'aside',
    data(){
      return{
        lists:[
          {title:'发现音乐',href:"#",isActive:true},
          {title:'私人FM',href:"#",isActive:false},
          {title:'MV',href:"#",isActive:false},
          {title:'下载管理',href:"#",isActive:false},
          
        ]
      }
    },
    methods:{
      changeBar(index){
        this.lists.forEach(function(val,ind){
          val.isActive=false;
          if(ind === index){
            val.isActive=true;
          }
        })
      }
    }
  } 
</script>
