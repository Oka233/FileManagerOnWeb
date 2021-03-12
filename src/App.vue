<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      user:null,
      width:null,
      height:null
    }
  },
  created() {
    if(this.user==null){
      this.$goRoute("/login");
    }
  },
  mounted() {
    window.onresize=()=>{
      return (() => {
        this.updateLayout();
      })();
    }
    this.$Message.config({
      background: true,
      top: 5,
      duration: 3,
    });

  },
  methods:{
    updateLayout(){
      this.width=document.body.clientWidth;
      this.height=document.body.offsetHeight;
      console.log(this.width,this.height);
    },
    test(){
      console.log(this.user);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /*margin-top: 60px;*/
}
html,body,#app{
  height: 100%;
}
*{
  font-family: "Helvetica Neue",Helvetica,"PingFang SC","Hiragino Sans GB","Microsoft YaHei","微软雅黑",Arial,sans-serif;
}
</style>
