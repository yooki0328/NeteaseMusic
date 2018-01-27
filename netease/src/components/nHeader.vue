<template>
<header>
<div class="logo"></div>
<div class="searchBox">
<input type="text" placeholder="搜索音乐,歌手,歌词,用户">
</div>
<div class="right_aside">
</div>
</header>
</template>
<style>
  header{
    height:60px;
    width:1000px;
    display:flex;
    align-items:center;
    margin-top:100px;
    background-color:#222225;
    justify-content:space-around;
  }
  .logo{
    width:160px;
    height:40px;
    background-image:url("../assets/topbar.png");
    background-repea:no-repeat;
    background-position:0px 0px;
  }
  .searchBox{
    margin-left:100px;
    height:35px;
    width:200px;
    background-image:url("../assets/topbar.png");
    background-repea:no-repeat;
    background-position:0px 75px;
  }
  .searchBox input{
    border:none;
    outline:none;
    width:160px;
    height:25px; 
    margin-top:5px;
    margin-left:30px;
    background-color:#EAEAEA;
    
  }

</style>
