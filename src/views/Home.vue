<template>
  <div class="home">
    <el-table
      :data="arr"
      stripe
      style="width: 100%">
      <el-table-column
        prop="id"
        label="学号"
        width="180">
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名"
        width="180">
      </el-table-column>
      <el-table-column
        prop="sex"
        label="性别">
      </el-table-column>
      <el-table-column label="操作">
      <template slot-scope="scope">
        <el-button
          size="mini"
          @click="handleEdit(scope.row)">编辑</el-button>
        <el-button
          size="mini"
          type="danger"
          @click="handleDelete(scope.row)">删除</el-button>
      </template>
    </el-table-column>
    </el-table>
    <button @click="abc">添加</button>
    <div v-show="lanf">
      <input type="text" v-model="alan.name">
      <input type="text" v-model="alan.sex">
      <input type="text" v-model="alan.state">
      <button @click="submit">添加</button>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
  components: {
    HelloWorld
  },
  data() {
    return {
      alan:{},
      arr:[],
      lanf:false 
    }
  },
  watch:{
    '$route'(){
      this.lan()
    }
  },        
  created(){
    this.lan()
  },
  methods:{
    lan(){
      this.$http.post('http://localhost:3000/',{state:this.$route.params.id},{emulateJSON:true}).then(e=>this.arr=e.body)
    },
    handleDelete(row) {
      alert(row)
      this.$http.post('http://localhost:3000/del',{id:row.id},{emulateJSON:true}).then(e=>this.rows=e.body)
      var _index = this.arr.indexOf(row)
      this.arr.splice(_index,1)
    },
    submit(e){
      this.$http.post('http://localhost:3000/add',this.alan,{emulateJSON:true}).then(()=>{})
    },
    abc(){
      this.lanf=!this.lanf
    }
  }
}
</script>
<style>

</style>
