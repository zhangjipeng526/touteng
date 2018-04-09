<template>
  <div id="app">
    <div id="nav">
      <el-menu
        class="el-menu-demo"
        mode="horizontal"
        @select="handleSelect"
        background-color="#545c64"
        text-color="#fff"
        active-text-color="#ffd04b">
        <el-menu-item index="1"><router-link to="/1">1705A</router-link></el-menu-item>
        <el-menu-item index="2"><router-link to="/2">代重修</router-link></el-menu-item>
        <el-menu-item index="3"><router-link to="/3">已重修</router-link></el-menu-item>
      </el-menu>
    </div>
    <router-view/>
    
    <div class="block">
      <el-carousel height="150px">
        <el-carousel-item v-for="item in 4" :key="item">
          <h3>{{ item }}</h3>
        </el-carousel-item>
      </el-carousel>
    </div>
  </div>
</template>

<script>
  export default{
    created(){
      if(this.$route.params.id==null){
        this.jgr="1"
      }else{
        this.jgr=parseInt(this.$route.params.id)+1+""
      }
    },
    watch:{
      '$route'(){
        if(this.$route.params.id==null){
        this.jgr="1"
      }else{
        this.jgr=parseInt(this.$route.params.id)+1+""
      }
      }
    },
    data() {
      return {
        jgr: ""
      };
    },
    methods:{
      handleSelect(key, keyPath) {
        console.log(key, keyPath);
      }
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
#nav li{
  padding: 0;
}

#nav a {
  font-weight: bold;
  display: inline-block;
  padding: 0 20px;
}
.el-carousel__item h3 {
    color: #475669;
    font-size: 14px;
    opacity: 0.75;
    line-height: 150px;
    text-align: center;
    margin: 0;
  }

  .el-carousel__item:nth-child(2n) {
     background-color: #99a9bf;
  }
  
  .el-carousel__item:nth-child(2n+1) {
     background-color: #d3dce6;
  }
</style>
