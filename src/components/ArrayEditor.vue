<template>
  <div id="arrayEditor">
    <h2>{{title}}</h2>
    <el-form id="form">
      <div v-for="(item,index) in items" :key="index">
        <el-button type="danger" @click="removeWorkHistory(index)" id="delete">删除</el-button>
        <el-form-item v-bind:label="labels[key]" v-for="(key,index) in keys" :key="index">
          <el-input v-model="item[key]"></el-input>
        </el-form-item>
      </div>
      <el-button type="primary" @click="addWorkHistory" id="add">添加</el-button>
    </el-form>
  </div>

</template>


<script>
  export default{
    props: ['items', 'labels', 'title', 'content'],
    computed: {
      keys(){
        return Object.keys(this.items[0])
      }
    },
    methods: {
      addWorkHistory: function () {
        this.items.push(this.content)
      },
      removeWorkHistory: function (index) {
        this.items.splice(index, 1)
        console.log('this.content', this.content)
      }
    }
  }
</script>
