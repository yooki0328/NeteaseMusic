<template>
<header>
<div class="logo"></div>
<div class="searchBox">
<input type="text" placeholder="搜索音乐,歌手,歌词,用户">
</div>
<div class="right_aside" @mouseenter="loginShowEnter" @mouseleave="loginShowLeave">
  <ul v-show="loginShow">
    <li v-for="(loginMethod,index) in loginMethods" :key="index">
      <!-- <a href="javascript:;">{{loginMethod.text}}</a> -->
      <el-button type="text" @click="phoneLogin">{{loginMethod.text}}</el-button>
      <!-- {{loginMethod.text}} -->
    </li>
  </ul>
  <a href="javascript:;" hidefocus=true class="header-login">登录</a>
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
    background-repeat:no-repeat;
    background-position:0px 0px;
  }
  .searchBox{
    margin-left:100px;
    height:35px;
    width:200px;
    background-image:url("../assets/topbar.png");
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
  .right_aside{
    height:45px;
    margin: 19px 0 0 20px;
    position: relative;
    padding: 0 22px 0 0;
    background-image:url("../assets/topbar.png");
    background-position: right -372px;
  }
  .right_aside ul{
    background: black;
    opacity: 0.8;
    list-style: none;
    position: absolute;
    top: 38px;
    right: -43px;
    width: 120px;
    color: #ccc;
  }
  .right_aside ul li a{
    display: block;
    border: #232323 1px solid;
    border-width: 1px 0;
    width: 100%;
    height: 38px;
    line-height: 39px;
    text-decoration: none;
    color: #ccc;
    font-size: 14px;
    padding-left: 24px;
  }
  .right_aside .header-login{
    text-decoration: none;
    display: block;
    color: #787878;
    font-size: 13px;
  }
</style>
<script>
export default {
  name: 'nheader',
  data(){
    return {
      loginShow: false,
      loginMethods: [
        {
          icon: '',
          text: '手机号登录'
        },
        {
          icon: '',
          text: '邮箱登录'
        },
        {
          icon: '',
          text: '微信登录'
        }
      ]
    }
  },
  methods: {
    loginShowEnter(){
      this.loginShow = true
    },
    loginShowLeave(){
      this.loginShow = false;
    },
    phoneLogin() {
        const h = this.$createElement;
        this.$msgbox({
          // title: '手机号登录',
          message: h('div', null, [
            h('div', {class: 'zbar'}, [
              h('div',{class: 'zttl'}, '手机号登录')
            ]),
            h('div',{class: 'zcnt'},[
              h('div',{class: 'n-log-box'},[
                h('div',null,'手机号'),
                h('div',null,'密码'),
                h('div',null,'登录')
              ])
            ])
          ]),
          showCancelButton: true,
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          beforeClose: (action, instance, done) => {
            if (action === 'confirm') {
              instance.confirmButtonLoading = true;
              instance.confirmButtonText = '执行中...';
              setTimeout(() => {
                done();
                setTimeout(() => {
                  instance.confirmButtonLoading = false;
                }, 300);
              }, 3000);
            } else {
              done();
            }
          }
        }).then(action => {
          this.$message({
            type: 'info',
            message: 'action: ' + action
          });
        });
      }
  }

}
</script>
